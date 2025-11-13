![Exported image](../../../attchments/Exported%20image%2020241213143448-0.png)

Using sudo we can run commands with any users privlage
 ![Exported image](../../../attchments/Exported%20image%2020241213143451-1.png)

List all commands I can with sudo
 ![Exported image](../../../attchments/Exported%20image%2020241213143453-2.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143459-3.png)

Now using vim we can read the shadow file crack the hash and privex  
We are privex using the intended fuctionality this is the METHOD 1
 
##### METHOD 2 Shell Escaping  
Directly getting the root shell
 ![Exported image](../../../attchments/Exported%20image%2020241213143502-4.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143504-5.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143507-6.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143509-7.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143512-8.png)  

We used vim and escape into /bin/bash to get a root shell
 ![Exported image](../../../attchments/Exported%20image%2020241213143514-9.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143520-10.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143522-11.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143527-12.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143529-13.png)   
EXPLOITING THE INTENDED FUCTIONALITY OF ANYTING TO PRIIVEX
   

#### METHOOD 3 enviromental variabels
   

WAT IS Eviromental variables  
What are libreries

![Exported image](../../../attchments/Exported%20image%2020241213143534-14.png)

Ld preload is a variable that will load before any other libbrariby files

![Exported image](../../../attchments/Exported%20image%2020241213143536-15.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143539-16.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143545-17.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143547-18.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143550-19.png)  
![Exported image](../../../attchments/Exported%20image%2020241213143555-20.png)

Ldd command tells us about the libreary files