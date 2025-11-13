
#winpriv #windows

----------------------------------------------SYSTEM enum-----------------------------------
 
BOX NAME = devel

![Exported image](../../../attchments/Exported%20image%2020241213160841-0.png) ![Exported image](../../../attchments/Exported%20image%2020241213160847-1.png)

systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"

![Exported image](../../../attchments/Exported%20image%2020241213160849-2.png)

hostname

![Exported image](../../../attchments/Exported%20image%2020241213160852-3.png)

wmic qfe

![Exported image](../../../attchments/Exported%20image%2020241213160854-4.png)

When was things patched what was installed when was installed

![Exported image](../../../attchments/Exported%20image%2020241213160856-5.png)
```
wmic qfe get Caption, Description, HotFixID, Installedon
```
wmic logicaldisk get caption,description,providername

![Exported image](../../../attchments/Exported%20image%2020241213160859-6.png)  

```
wmic logicaldisk get caption,description,providername
```
-------------------------------USER ENUM-------------------------------------
 ![Exported image](../../../attchments/Exported%20image%2020241213160902-7.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160907-8.png)

whoami /priv

![Exported image](../../../attchments/Exported%20image%2020241213160910-9.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160912-10.png)

It will tell you how mmany users are there

![Exported image](../../../attchments/Exported%20image%2020241213160914-11.png)

It will tell you information about the user
   
![Exported image](../../../attchments/Exported%20image%2020241213160916-12.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160918-13.png)     

-----------------------------NETWORK ENUM----------------------------------------
 ![Exported image](../../../attchments/Exported%20image%2020241213160920-14.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160925-15.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160927-16.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160929-17.png)   
![Exported image](../../../attchments/Exported%20image%2020241213160931-18.png) ![Exported image](../../../attchments/Exported%20image%2020241213160933-19.png) ![Exported image](../../../attchments/Exported%20image%2020241213160935-20.png)
   

-------------------------------PASSWORD HUNTING------------------------------------
 ![Exported image](../../../attchments/Exported%20image%2020241213160937-21.png)

findstr /si password *.txt

![Exported image](../../../attchments/Exported%20image%2020241213160942-22.png)

findstr /si password *.txt *.ini *.config

![Exported image](../../../attchments/Exported%20image%2020241213160944-23.png)     

--------------------------------------------AV and Firewall ENUM---------------------------------
   
![Exported image](../../../attchments/Exported%20image%2020241213160946-24.png)

Sc in service control in above we are figuring out windows defender
 ![Exported image](../../../attchments/Exported%20image%2020241213160949-25.png)

This is going to tell you all the services running on the machine  
sc queryex type= service

![Exported image](../../../attchments/Exported%20image%2020241213160950-26.png)

netsh advfirewall firewall dump

![Exported image](../../../attchments/Exported%20image%2020241213160954-27.png)  
![Exported image](../../../attchments/Exported%20image%2020241213160956-28.png)

Use this for finding specific port