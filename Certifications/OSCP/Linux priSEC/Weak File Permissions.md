![[Exported image 20241213143259-0.png|Exported image]]

3 types of IMP Files  
(I)/etc/passwd  
(II)/etc/shadow  
(III)/etc/sudoers
   

##### METHOD 1
   
![[Exported image 20241213143303-1.png|Exported image]]

In above image we have read and write permissions

![[Exported image 20241213143309-2.png|Exported image]]  
![[Exported image 20241213143315-3.png|Exported image]]

This is passwd In hash format it starts with : and ends with :  
We can copy this and crack this

![[Exported image 20241213143319-4.png|Exported image]]

Now we can login with the password

![[Exported image 20241213143321-5.png|Exported image]]  

##### METHOD 2
 ![[Exported image 20241213143324-6.png|Exported image]]   ![[Exported image 20241213143327-7.png|Exported image]]  
![[Exported image 20241213143330-8.png|Exported image]]

Now we can create a our own hash and repalce it with the root hash so we alredy know the password

![[Exported image 20241213143336-9.png|Exported image]]

-6 represeent $6$ for SHA-512 format

![[Exported image 20241213143340-10.png|Exported image]]  
![[Exported image 20241213143342-11.png|Exported image]]  
![[Exported image 20241213143345-12.png|Exported image]]  
![[Exported image 20241213143348-13.png|Exported image]]

I changed my password to hello and became root
 
#### MEHTOD 1 /etc/passwd
 
If you have write privlga on /etc/passwd what can you do
 ![[Exported image 20241213143351-14.png|Exported image]]  
![[Exported image 20241213143354-15.png|Exported image]]

That X that is highlighted in the image telss linux the the passwd of that user is stored in the shadow file
 
But if there is no x then linux thinks that the user has no password and can autologin without a password
 ![[Exported image 20241213143411-16.png|Exported image]]  

### METHOD 2 /etc/passwd
 ![[Exported image 20241213143413-17.png|Exported image]]  

You can also replace the x with your own passwd hash so linux will directly take the passwd from passwd file and it will not go to shadow file to get the hash
 ![[Exported image 20241213143416-18.png|Exported image]]  
![[Exported image 20241213143418-19.png|Exported image]]  
![[Exported image 20241213143421-20.png|Exported image]]  

#### MTHOD 3 /etc/passwd
 
We can also create ouur own root user and give it a new hash passwd and also give it the uid of the root user

![[Exported image 20241213143424-21.png|Exported image]]

We created a root user called toor

![[Exported image 20241213143427-22.png|Exported image]]  

### METHOD 1 /etc/sudoers
 ![[Exported image 20241213143433-23.png|Exported image]]

We only have read permissions

![[Exported image 20241213143436-24.png|Exported image]]

Now we have given read and write
 
If we enter a shell and the sudoers filer has rw perm what to do

![[Exported image 20241213143439-25.png|Exported image]]  
![[Exported image 20241213143442-26.png|Exported image]]