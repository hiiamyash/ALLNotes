#windows  #active #cheetsheet 

# Enumration



# Users & Computers

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

Get a list of users in the current domain

```
Get-DomainUser
Get-DomainUser -Identity student1
Get-ADUser -Filter * -Properties *
Get-ADUser -Identity student1 -Properties *
```

Get list of all properties for users in the current domain

```
Get-DomainUser -Identity student1 -Properties *
Get-DomainUser -Properties samaccountname,logonCount
Get-ADUser -Filter * -Properties * | select -First 1 | Get-Member -
MemberType *Property | select Name
Get-ADUser -Filter * -Properties * | select
name,logoncount,@{expression={[datetime]::fromFileTime($_.pwdlastset)}}
```

Search for a particular string in a user's attributes:


```
Get-DomainUser -LDAPFilter "Description=*built*" | Select name,Description

Get-ADUser -Filter 'Description -like "*built*"' -
Properties Description | select name,Description
```

```
Get a list of computers in the current domain

Get-DomainComputer | select Name
Get-DomainComputer -OperatingSystem "*Server 2022*"
Get-DomainComputer -Ping
Get-ADComputer -Filter * | select Name
Get-ADComputer -Filter * -Properties *
Get-ADComputer -Filter 'OperatingSystem -like "*Server 2022*"' -
Properties OperatingSystem | select Name,OperatingSystem
Get-ADComputer -Filter * -Properties DNSHostName | %{Test-
Connection -Count 1 -ComputerName $_.DNSHostName}
```


# Domain

Get current domain
```
Get-Domain
```

Get object of another domain

```
Get-Domain -Domain moneycorp.local
```

```
Get-ADDomain -Identity moneycorp.local
```

Get domain SID for the current domain

```
Get-DomainSID
```


```
(Get-ADDomain).DomainSID
```

Get domain policy for the current domain

```
Get-DomainPolicyData
```


```
(Get-DomainPolicyData).systemaccess
```

Get domain policy for another domain

```
(Get-DomainPolicyData -domain moneycorp.local).systemaccess
```

Get domain controllers for the current domain


```
Get-DomainController
```


```
Get-ADDomainController
```

# Groups

```
Get all the groups in the current domain
Get-DomainGroup | select Name
Get-DomainGroup -Domain <targetdomain>
Get-ADGroup -Filter * | select Name
Get-ADGroup -Filter * -Properties
```

Get all groups containing the word "admin" in group name

```
Get-DomainGroup *admin*
Get-ADGroup -Filter 'Name -like "*admin*"' | select Name
```

Get all the members of the Domain Admins group


```
Get-DomainGroupMember -Identity "Domain Admins" -Recurse
Get-ADGroupMember -Identity "Domain Admins" -Recursive
```


# GPOs & OU

```
Get-NetOU

Get-ADOrganizationalUnit -Filter * | Select-Object Name, DistinguishedName

the above will give the name of OU's
```




---
## KRB5 

```
nxc smb frizzdc.frizz.htb -k -u f.frizzle -p Jenni_Luvs_Magic23 --generate-krb5-file frizz.krb
```

Above will create an file called frizz.krb now if you copy that as krb5.conf to /etc then active directory can communicate better to your machine
```
sudo cp frizz.krb5 /etc/krb5.conf
```

OR 
```
export KRB5_CONFIG=$(pwd)/frizz.krb5
```


`ssh Kerberos Authnetication`

```
getTGT.py frizz.htb/f.frizzle:Jenni_Luvs_Magic23
```

Yow will get an f.frizzle.ccache file

```
export KRB5CCNAME=$(pwd)/f.frizzle.ccache
```

```
ssh -K f.frizzle@frizzdc.frizz.htb
```
make sure to use the actual name of the host 

