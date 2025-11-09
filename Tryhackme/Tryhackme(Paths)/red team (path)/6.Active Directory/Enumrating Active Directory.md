#windows #active 

# Net commands


this command will give you alll the users in the domain
```
net user /domain
```

Info about an specific user

```
net user zoe.marshall /domain
```

this command will give you info about how many memebers are there in an specific group
```
net group "Tier 1 Admins" /domain
```

info about Password policy 

```
net accounts /domain
```



# Powershell


## Users

Enumrate ad users
```
Get-ADUser -Identity gordon.stevens -Server za.tryhackme.com -Properties *
```

Enumarate all users
```
Get-ADUser -Filter * -Server za.tryhackme.com -Properties *
```

Find Users with an alike name
```
Get-ADUser -Filter 'Name -like "*stevens"' -Server za.tryhackme.com | Format-Table Name,SamAccountName -A
```

## Groups

Enumrate groups 
```
Get-ADGroup -Identity Administrators -Server za.tryhackme.com

Get-ADGroup -Filter * -Server za.tryhackme.com

```

if want to kown all memebers fo an certain group

```
Get-ADGroupMember -Identity Administrators -Server za.tryhackme.com
```

## Objects


info about AD objects 
```
$ChangeDate = New-Object DateTime(2022, 02, 28, 12, 00, 00) 


Get-ADObject -Filter 'whenChanged -gt $ChangeDate' -includeDeletedObjects -Server za.tryhackme.com
```

Avoid these accounts in password spraying attacks because you can lock them out 
```
Get-ADObject -Filter 'badPwdCount -gt 0' -Server za.tryhackme.com
```

## Domain

```
Get-ADDomain -Server za.tryhackme.com
```

## Change password of an AD User

```
Set-ADAccountPassword -Identity gordon.stevens -Server za.tryhackme.com -OldPassword (ConvertTo-SecureString -AsPlaintext "enterOLDpasswd" -force) -NewPassword (ConvertTo-SecureString -AsPlainText "enterNEWpassword" -Force)
```
