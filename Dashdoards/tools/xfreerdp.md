
```bash
xfreerdp /v:10.10.10.100 /u:Administrator /p:P@ssw0rd123
```


```
xfreerdp /v:10.10.10.100 /u:Administrator /pth:aad3b435b51404eeaad3b435b51404ee
```
`Pass the hash`


```
xfreerdp /v:10.10.10.100 /u:svc_user /p:Sup3rS3cret! /cert:ignore
```
`Ignore the cert`


```
xfreerdp /v:10.10.10.100 /u:Administrator /p:P@ssw0rd123 /cert:ignore /size:1600x900 /drive:share,/home/antivenom/htb_files
```
`With Drive Sharing`


```
 xfreerdp /v:10.129.204.23 /u:Administrator /p:AnotherC0mpl3xP4$$ /cert:ignore -sec-nla
```

```
xfreerdp3 /v:10.129.204.23 /u:Administrator /p:AnotherC0mpl3xP4$$ /cert:ignore /sec:nla:off
```

