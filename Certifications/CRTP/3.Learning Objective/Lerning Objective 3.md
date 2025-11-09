#windows
#active 

![Pasted image 20250327234739](Pasted%20image%2020250327234739.png)

![Pasted image 20250327234811](Pasted%20image%2020250327234811.png)

```
Get-NetOU

Get-ADOrganizationalUnit -Filter * | Select-Object Name, DistinguishedName

the above will give the name of OU's
```

```
Get-ADOrganizationalUnit -Filter "Name -eq 'DevOps'" | ForEach-Object { Get-ADComputer -SearchBase $_.DistinguishedName -Filter * } | Select-Object Name

the above command will be use to find how many computers are in the any OU
```

```
Get-NetGPO

this above command will give you all the GPO's

Get
```

**if you want to enumrate what GPO's are being applied on the Specific OU you are targeting then find out that OU's  gplink and then use one more command using that gplink


```


(Get-ADOrganizationalUnit -Filter 'Name -eq "DevOps"' -Properties gplink).gplink

the abpve commad will give you the gplink which are just jumbel num and alphaapets


Get-ADObject -Filter {ObjectClass -eq "groupPolicyContainer"} | Where-Object { $_.Name -match "6AC1786C-016F-11D2-945F-00C04fB984F9" }

put the gplink code in this command to get GPO's being applied on 
```

