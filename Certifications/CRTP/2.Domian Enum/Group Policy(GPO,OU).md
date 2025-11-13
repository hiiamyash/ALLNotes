
#active #windows 


![[../../../attchments/Pasted image 20250327092743.png]]

**using policy you can control what access does the User have and how i machiine is used

![[../../../attchments/Pasted image 20250327093029.png]]

![[../../../attchments/Pasted image 20250327152557.png]]

![[../../../attchments/Pasted image 20250327161726.png]]
![[../../../attchments/Pasted image 20250327161933.png]]
**if you are trying to find an GPO for an particular OU then do the above


### **Definition of Organizational Units (OUs) in Active Directory**

An **Organizational Unit (OU)** in **Active Directory (AD)** is a logical container used to organize and manage users, computers, and other AD objects within a domain. OUs help in applying **Group Policies** and delegating administrative control in a structured way.

---

### **Example: Understanding OUs Easily**

Imagine your company is like a **big office building**. Inside this building, different **departments** exist, such as:

- **HR (Human Resources)**
    
- **IT (Information Technology)**
    
- **Finance**
    

Each of these departments needs different security rules, access permissions, and policies. In **Active Directory**, you can create **Organizational Units (OUs)** for each department:

```scss
Company.com
│
├── HR (OU)
│   ├── Alice (User)
│   ├── Bob (User)
│   ├── HR-Computer1 (Computer)
│
├── IT (OU)
│   ├── Charlie (User)
│   ├── IT-Computer1 (Computer)
│   ├── IT-Server (Server)
│
├── Finance (OU)
│   ├── Dave (User)
│   ├── Finance-Computer1 (Computer)

```

```
Get-NetOU

Get-ADOrganizationalUnit -Filter * | Select-Object Name, DistinguishedName

Get-ADOrganizationalUnit -Filter * | Select-Object Name

Get-GPO -Guid "0BF8D01C-1F62-4BDC-958C-57140B67D147"

```




GPOs are distributed to the network via a network share called `SYSVOL`

C:\Windows\SYSVOL\sysvol\

```
PS C:\> gpupdate /force

above command will immediatelt update the GPO

```