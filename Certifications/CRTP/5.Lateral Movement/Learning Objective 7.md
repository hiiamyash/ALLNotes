#windows
#active 

![[../../../attchments/Pasted image 20250407102557.png]]

# Q1


![[../../../attchments/Pasted image 20250407103605.png]]

in the above image we can see dcorp\svcadmin which we knew is an domain adminisrtrator because of the bloodhound and he has an session on this machice

![[../../../attchments/Pasted image 20250407103941.png]]

c
we are downloading and executing sbloggingbypass.txt


![[../../../attchments/Pasted image 20250407104004.png]]

Powerview.ps1

![[../../../attchments/Pasted image 20250407113644.png]]
using the abpve command we are able to FInd the Domain user account in the new reverse shell we got 

# Q2
![[../../../attchments/Pasted image 20250407113743.png]]

now as dcorp-ci we are able to execute commands on Dcorp-MGMt that means we have aadminsitrative privlages on dcorp-mgmt



![[../../../attchments/Pasted image 20250407105250.png]]

in the above command we downloded the loader.exe on the dcorp-ci then copy it to dcorp-mgmt beacue we have adminsitrative right over it

in the above we also downloaded safteykatz.exe and execute it on the dcorp-mgmt to extract creds


![[../../../attchments/Pasted image 20250407114412.png]]

we need the aes256_hmac

![[../../../attchments/Pasted image 20250407114636.png]]

in this above command we will use svcadmin ace256 to get an cmd session with student1 but with svcadmin privilages 

![[../../../attchments/Pasted image 20250407114810.png]]

you can see above we are able to access the Domain controller as student 1 but we have svcadmin rights



# Q3

What is Derivative Local admin

![[../../../attchments/Pasted image 20250407134310.png]]

if studenx has admin access over dcorp-adminsrv and there is an user called srvadmin on dcrop-adminsrv which has admin access over dcorp-mgmt that means student x has admin access over dcorp-mgmt


![[../../../attchments/Pasted image 20250407141755.png]]

lets suppose we have to block AMSI that we will use the above queary but it throws an error because the powershell session is running on constrainedLanguagemode  beauuse the applocker is forcing it to run in constrainedLanguagemode 

then we have to bypass apploacker or disable it

![[../../../attchments/Pasted image 20250407142057.png]]we used the above command o cheack for Applocker


![[../../../attchments/Pasted image 20250407142150.png]]
we used this command to get Rulecollections

![[../../../attchments/Pasted image 20250407142250.png]]
if we see this S-1-1-0 that means allow everyone


![[../../../attchments/Pasted image 20250407142409.png]]
seeing the above image we can tell that anyone can run any script from Programfiles and WINDIR directory



**Applocker works on application allow listing similar to an whitelist which will alow only good code to run

![[../../../attchments/Pasted image 20250410150126.png]]

now we are copying mimi.psqq which is an ofusated version of mimikatz to the Program files directory

![[../../../attchments/Pasted image 20250410151007.png]]
the above sript in executing an mimikatz command called sekurlsa::keys


![[../../../attchments/Pasted image 20250410151148.png]]


![[../../../attchments/Pasted image 20250412134713.png]]
![[../../../attchments/Pasted image 20250412134806.png]]
we are checking if adminsrv has administrative access over dcorp-mgmt

yes it has administrative access


![[../../../attchments/Pasted image 20250412134944.png]]
now we are copying the loder.exe to mgmt and setting up over port forwarding

![[../../../attchments/Pasted image 20250412135108.png]]

![[../../../attchments/Pasted image 20250412135639.png]]

