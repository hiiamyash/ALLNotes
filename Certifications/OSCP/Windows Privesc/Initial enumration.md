
#winpriv #windows

----------------------------------------------SYSTEM enum-----------------------------------
 
BOX NAME = devel

![[../../../attchments/Exported image 20241213160841-0.png|Exported image]] ![[../../../attchments/Exported image 20241213160847-1.png|Exported image]]

systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"

![[../../../attchments/Exported image 20241213160849-2.png|Exported image]]

hostname

![[../../../attchments/Exported image 20241213160852-3.png|Exported image]]

wmic qfe

![[../../../attchments/Exported image 20241213160854-4.png|Exported image]]

When was things patched what was installed when was installed

![[../../../attchments/Exported image 20241213160856-5.png|Exported image]]
```
wmic qfe get Caption, Description, HotFixID, Installedon
```
wmic logicaldisk get caption,description,providername

![[../../../attchments/Exported image 20241213160859-6.png|Exported image]]  

```
wmic logicaldisk get caption,description,providername
```
-------------------------------USER ENUM-------------------------------------
 ![[../../../attchments/Exported image 20241213160902-7.png|Exported image]]  
![[../../../attchments/Exported image 20241213160907-8.png|Exported image]]

whoami /priv

![[../../../attchments/Exported image 20241213160910-9.png|Exported image]]  
![[../../../attchments/Exported image 20241213160912-10.png|Exported image]]

It will tell you how mmany users are there

![[../../../attchments/Exported image 20241213160914-11.png|Exported image]]

It will tell you information about the user
   
![[../../../attchments/Exported image 20241213160916-12.png|Exported image]]  
![[../../../attchments/Exported image 20241213160918-13.png|Exported image]]     

-----------------------------NETWORK ENUM----------------------------------------
 ![[../../../attchments/Exported image 20241213160920-14.png|Exported image]]  
![[../../../attchments/Exported image 20241213160925-15.png|Exported image]]  
![[../../../attchments/Exported image 20241213160927-16.png|Exported image]]  
![[../../../attchments/Exported image 20241213160929-17.png|Exported image]]   
![[../../../attchments/Exported image 20241213160931-18.png|Exported image]] ![[../../../attchments/Exported image 20241213160933-19.png|Exported image]] ![[../../../attchments/Exported image 20241213160935-20.png|Exported image]]
   

-------------------------------PASSWORD HUNTING------------------------------------
 ![[../../../attchments/Exported image 20241213160937-21.png|Exported image]]

findstr /si password *.txt

![[../../../attchments/Exported image 20241213160942-22.png|Exported image]]

findstr /si password *.txt *.ini *.config

![[../../../attchments/Exported image 20241213160944-23.png|Exported image]]     

--------------------------------------------AV and Firewall ENUM---------------------------------
   
![[../../../attchments/Exported image 20241213160946-24.png|Exported image]]

Sc in service control in above we are figuring out windows defender
 ![[../../../attchments/Exported image 20241213160949-25.png|Exported image]]

This is going to tell you all the services running on the machine  
sc queryex type= service

![[../../../attchments/Exported image 20241213160950-26.png|Exported image]]

netsh advfirewall firewall dump

![[../../../attchments/Exported image 20241213160954-27.png|Exported image]]  
![[../../../attchments/Exported image 20241213160956-28.png|Exported image]]

Use this for finding specific port