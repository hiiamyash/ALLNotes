![[../../../attchments/Exported image 20241213143448-0.png|Exported image]]

Using sudo we can run commands with any users privlage
 ![[../../../attchments/Exported image 20241213143451-1.png|Exported image]]

List all commands I can with sudo
 ![[../../../attchments/Exported image 20241213143453-2.png|Exported image]]  
![[../../../attchments/Exported image 20241213143459-3.png|Exported image]]

Now using vim we can read the shadow file crack the hash and privex  
We are privex using the intended fuctionality this is the METHOD 1
 
##### METHOD 2 Shell Escaping  
Directly getting the root shell
 ![[../../../attchments/Exported image 20241213143502-4.png|Exported image]]  
![[../../../attchments/Exported image 20241213143504-5.png|Exported image]]  
![[../../../attchments/Exported image 20241213143507-6.png|Exported image]]  
![[../../../attchments/Exported image 20241213143509-7.png|Exported image]]  
![[../../../attchments/Exported image 20241213143512-8.png|Exported image]]  

We used vim and escape into /bin/bash to get a root shell
 ![[../../../attchments/Exported image 20241213143514-9.png|Exported image]]  
![[../../../attchments/Exported image 20241213143520-10.png|Exported image]]  
![[../../../attchments/Exported image 20241213143522-11.png|Exported image]]  
![[../../../attchments/Exported image 20241213143527-12.png|Exported image]]  
![[../../../attchments/Exported image 20241213143529-13.png|Exported image]]   
EXPLOITING THE INTENDED FUCTIONALITY OF ANYTING TO PRIIVEX
   

#### METHOOD 3 enviromental variabels
   

WAT IS Eviromental variables  
What are libreries

![[../../../attchments/Exported image 20241213143534-14.png|Exported image]]

Ld preload is a variable that will load before any other libbrariby files

![[../../../attchments/Exported image 20241213143536-15.png|Exported image]]  
![[../../../attchments/Exported image 20241213143539-16.png|Exported image]]  
![[../../../attchments/Exported image 20241213143545-17.png|Exported image]]  
![[../../../attchments/Exported image 20241213143547-18.png|Exported image]]  
![[../../../attchments/Exported image 20241213143550-19.png|Exported image]]  
![[../../../attchments/Exported image 20241213143555-20.png|Exported image]]

Ldd command tells us about the libreary files