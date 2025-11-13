#basics #reverse

![Exported image](../../attchments/Exported%20image%2020241213183851-0.png)

Kernal acts as a bridge betwwen software and hardware kernal does everything exexcting commands openninfg files  
For example lets suppose there is an file manager and we click on a file to open it the kernal take tehe reqyest from user mode and reaches out to the memroyr where that file is stored then displayes that to the user
 
----------How do user mode and kernal Commucate ??
 
USING SYSTEM CALLS

![Exported image](../../attchments/Exported%20image%2020241213183853-1.png)

First user start the process then user mode makes sysytem calls to the kernal  
System calls intstructs kernal what to do where to write the file when to read it when to start coping the file
   

-------------------This is the place where system calls are saved

![Exported image](../../attchments/Exported%20image%2020241213183856-2.png) ![Exported image](../../attchments/Exported%20image%2020241213183858-3.png)  

-----------C language is used to make sysytem calls

![Exported image](../../attchments/Exported%20image%2020241213183901-4.png)

In this above command we are trying to see the maual page of the system call of write
 ![Exported image](../../attchments/Exported%20image%2020241213183907-5.png)  
![Exported image](../../attchments/Exported%20image%2020241213183910-6.png)

Fd ----------types  
Standard input(used for read)----number to represent is 0  
Standard output(used to write)----number to represent is 1  
Standard error(used to write) ----number to represent is 2  

![Exported image](../../attchments/Exported%20image%2020241213183913-7.png)  
![Exported image](../../attchments/Exported%20image%2020241213183915-8.png)  
![Exported image](../../attchments/Exported%20image%2020241213183918-9.png)  
![Exported image](../../attchments/Exported%20image%2020241213183920-10.png)  
![Exported image](../../attchments/Exported%20image%2020241213183922-11.png)  
![Exported image](../../attchments/Exported%20image%2020241213183927-12.png)  
![Exported image](../../attchments/Exported%20image%2020241213183930-13.png)  
![Exported image](../../attchments/Exported%20image%2020241213183932-14.png)

Write and exit are tw system calls that we are calling

![Exported image](../../attchments/Exported%20image%2020241213183934-15.png)  
![Exported image](../../attchments/Exported%20image%2020241213183936-16.png)  
![Exported image](../../attchments/Exported%20image%2020241213183939-17.png)  
![Exported image](../../attchments/Exported%20image%2020241213183942-18.png)

In exit syatem call If the program run succesfully it is going to print 11 if not then it is going to print any other number

![Exported image](../../attchments/Exported%20image%2020241213183947-19.png)   ![Exported image](../../attchments/Exported%20image%2020241213183950-20.png)  

![Exported image](../../attchments/Exported%20image%2020241213183952-21.png)