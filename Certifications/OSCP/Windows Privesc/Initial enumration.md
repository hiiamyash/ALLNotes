
#winpriv #windows

----------------------------------------------SYSTEM enum-----------------------------------
 
BOX NAME = devel

![[Exported image 20241213160841-0.png|Exported image]] ![[Exported image 20241213160847-1.png|Exported image]]

systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"

![[Exported image 20241213160849-2.png|Exported image]]

hostname

![[Exported image 20241213160852-3.png|Exported image]]

wmic qfe

![[Exported image 20241213160854-4.png|Exported image]]

When was things patched what was installed when was installed

![[Exported image 20241213160856-5.png|Exported image]]
```
wmic qfe get Caption, Description, HotFixID, Installedon
```
wmic logicaldisk get caption,description,providername

![[Exported image 20241213160859-6.png|Exported image]]  

```
wmic logicaldisk get caption,description,providername
```
-------------------------------USER ENUM-------------------------------------
 ![[Exported image 20241213160902-7.png|Exported image]]  
![[Exported image 20241213160907-8.png|Exported image]]

whoami /priv

![[Exported image 20241213160910-9.png|Exported image]]  
![[Exported image 20241213160912-10.png|Exported image]]

It will tell you how mmany users are there

![[Exported image 20241213160914-11.png|Exported image]]

It will tell you information about the user
   
![[Exported image 20241213160916-12.png|Exported image]]  
![[Exported image 20241213160918-13.png|Exported image]]     

-----------------------------NETWORK ENUM----------------------------------------
 ![[Exported image 20241213160920-14.png|Exported image]]  
![[Exported image 20241213160925-15.png|Exported image]]  
![[Exported image 20241213160927-16.png|Exported image]]  
![[Exported image 20241213160929-17.png|Exported image]]   
![[Exported image 20241213160931-18.png|Exported image]] ![[Exported image 20241213160933-19.png|Exported image]] ![[Exported image 20241213160935-20.png|Exported image]]
   

-------------------------------PASSWORD HUNTING------------------------------------
 ![[Exported image 20241213160937-21.png|Exported image]]

findstr /si password *.txt

![[Exported image 20241213160942-22.png|Exported image]]

findstr /si password *.txt *.ini *.config

![[Exported image 20241213160944-23.png|Exported image]]     

--------------------------------------------AV and Firewall ENUM---------------------------------
   
![[Exported image 20241213160946-24.png|Exported image]]

Sc in service control in above we are figuring out windows defender
 ![[Exported image 20241213160949-25.png|Exported image]]

This is going to tell you all the services running on the machine  
sc queryex type= service

![[Exported image 20241213160950-26.png|Exported image]]

netsh advfirewall firewall dump

![[Exported image 20241213160954-27.png|Exported image]]  
![[Exported image 20241213160956-28.png|Exported image]]

Use this for finding specific port