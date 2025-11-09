![Exported image](Exported%20image%2020241213143259-0.png)

3 types of IMP Files  
(I)/etc/passwd  
(II)/etc/shadow  
(III)/etc/sudoers
   

##### METHOD 1
   
![Exported image](Exported%20image%2020241213143303-1.png)

In above image we have read and write permissions

![Exported image](Exported%20image%2020241213143309-2.png)  
![Exported image](Exported%20image%2020241213143315-3.png)

This is passwd In hash format it starts with : and ends with :  
We can copy this and crack this

![Exported image](Exported%20image%2020241213143319-4.png)

Now we can login with the password

![Exported image](Exported%20image%2020241213143321-5.png)  

##### METHOD 2
 ![Exported image](Exported%20image%2020241213143324-6.png)   ![Exported image](Exported%20image%2020241213143327-7.png)  
![Exported image](Exported%20image%2020241213143330-8.png)

Now we can create a our own hash and repalce it with the root hash so we alredy know the password

![Exported image](Exported%20image%2020241213143336-9.png)

-6 represeent $6$ for SHA-512 format

![Exported image](Exported%20image%2020241213143340-10.png)  
![Exported image](Exported%20image%2020241213143342-11.png)  
![Exported image](Exported%20image%2020241213143345-12.png)  
![Exported image](Exported%20image%2020241213143348-13.png)

I changed my password to hello and became root
 
#### MEHTOD 1 /etc/passwd
 
If you have write privlga on /etc/passwd what can you do
 ![Exported image](Exported%20image%2020241213143351-14.png)  
![Exported image](Exported%20image%2020241213143354-15.png)

That X that is highlighted in the image telss linux the the passwd of that user is stored in the shadow file
 
But if there is no x then linux thinks that the user has no password and can autologin without a password
 ![Exported image](Exported%20image%2020241213143411-16.png)  

### METHOD 2 /etc/passwd
 ![Exported image](Exported%20image%2020241213143413-17.png)  

You can also replace the x with your own passwd hash so linux will directly take the passwd from passwd file and it will not go to shadow file to get the hash
 ![Exported image](Exported%20image%2020241213143416-18.png)  
![Exported image](Exported%20image%2020241213143418-19.png)  
![Exported image](Exported%20image%2020241213143421-20.png)  

#### MTHOD 3 /etc/passwd
 
We can also create ouur own root user and give it a new hash passwd and also give it the uid of the root user

![Exported image](Exported%20image%2020241213143424-21.png)

We created a root user called toor

![Exported image](Exported%20image%2020241213143427-22.png)  

### METHOD 1 /etc/sudoers
 ![Exported image](Exported%20image%2020241213143433-23.png)

We only have read permissions

![Exported image](Exported%20image%2020241213143436-24.png)

Now we have given read and write
 
If we enter a shell and the sudoers filer has rw perm what to do

![Exported image](Exported%20image%2020241213143439-25.png)  
![Exported image](Exported%20image%2020241213143442-26.png)