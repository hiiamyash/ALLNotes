![Exported image](Exported%20image%2020241213160713-0.png)  

We have a hint that there can be a path transversal  
Vernability
   
![Exported image](Exported%20image%2020241213160716-1.png)

The parameter page is in the file index.php  
Now we can see how the index.php is working it is first replacing ../ with "" and ./ with "" and the starting has to be with a alpabet
 
So this wiil be our payload  
assets/…..///…..///…..///…..///etc/passwd
 
We use assets and then / to escape from assets

![Exported image](Exported%20image%2020241213160718-2.png)  
![Exported image](Exported%20image%2020241213160721-3.png)

Now we are reading the .bash_history file in our blue user directory and we can see how red team is using hashcat to generate password list from .reminder file
 
Now lets check the .reminder file

![Exported image](Exported%20image%2020241213160723-4.png)

Here we have got the sample they have used to genetrate their passlist  
Now we will do the same

![Exported image](Exported%20image%2020241213160728-5.png)  
![Exported image](Exported%20image%2020241213160730-6.png)

Now we will use hydra to brute force the ssh
 ![Exported image](Exported%20image%2020241213160733-7.png)  
![Exported image](Exported%20image%2020241213160736-8.png)  
![Exported image](Exported%20image%2020241213160738-9.png)

We have gotten a shell