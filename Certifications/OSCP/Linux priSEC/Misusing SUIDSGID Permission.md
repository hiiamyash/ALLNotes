![[Exported image 20241213143756-0.png|Exported image]]  
SUID set user id  
Any user can run the file that has suid with root privlages
 
TO FIND SUID FILES

![[Exported image 20241213143801-1.png|Exported image]]  

####### EXPLOITAION OF SUID
 
### METHOD 1  
Commands intended functionality
 ![[Exported image 20241213143804-2.png|Exported image]]  
![[Exported image 20241213143807-3.png|Exported image]]  
![[Exported image 20241213143809-4.png|Exported image]]  
![[Exported image 20241213143812-5.png|Exported image]]

We exploited the intended functionality od the cat command to exploit the machine and priv ex
 
### METHOD 2  
Shell Escaping
 ![[Exported image 20241213143815-6.png|Exported image]]  
![[Exported image 20241213143817-7.png|Exported image]]  
![[Exported image 20241213143823-8.png|Exported image]]  
![[Exported image 20241213143825-9.png|Exported image]]  

### METHOD 3  
PATH Variable injection(Custom file 1)

![[Exported image 20241213143828-10.png|Exported image]]  
![[Exported image 20241213143831-11.png|Exported image]]

This is a custom file which is not found in gtfo bins this files are mainly found in hard and medium ctf
 ![[Exported image 20241213143834-12.png|Exported image]]

Strings command gives everyting that is human readable inside that file
 
We can see that suid-env is calling an script called service  
Now wehave to check wether we can exploit this or not
 ![[Exported image 20241213143835-13.png|Exported image]]  

Env command outputs all the enviromental variable
 ![[Exported image 20241213143839-14.png|Exported image]]  
![[Exported image 20241213143846-15.png|Exported image]]  
![[Exported image 20241213143849-16.png|Exported image]]  
![[Exported image 20241213143852-17.png|Exported image]]   
### METHOD 4  
Shared file overtake
 ![[Exported image 20241213143854-18.png|Exported image]]

So files are called shared object files they are like libreary filer example when you write code you use import socket so soket is a library
 ![[Exported image 20241213143857-19.png|Exported image]]  
![[Exported image 20241213143900-20.png|Exported image]]  
![[Exported image 20241213143902-21.png|Exported image]]  
![[Exported image 20241213143908-22.png|Exported image]]  
![[Exported image 20241213143911-23.png|Exported image]]  
![[Exported image 20241213143913-24.png|Exported image]]  
![[Exported image 20241213143917-25.png|Exported image]]  
![[Exported image 20241213143919-26.png|Exported image]]  
![[Exported image 20241213143921-27.png|Exported image]]





