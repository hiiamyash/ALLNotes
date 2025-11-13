#active 
#windows
![[../../../attchments/Pasted image 20250404081655.png]]

![[../../../attchments/Pasted image 20250404081801.png]]

gpcfilesyspath is the policy we are going to modify

![[../../../attchments/Pasted image 20250404081903.png]]

you can see that the Devops user that has writeDacl perm on the Devopsgroup policy

![[../../../attchments/Pasted image 20250404082756.png]]

-t ldaps:ip 

the ip is of the doamin controller

and -wh ip is the ipp of our w=machine

![[../../../attchments/Pasted image 20250404083229.png]]

![[../../../attchments/Pasted image 20250404083240.png]]

make this powershell command as the shortcut

![[../../../attchments/Pasted image 20250404083411.png]]

this is the shortcut we created
now we will copy this to the dc-cropci//AI share

![[../../../attchments/Pasted image 20250404083624.png]]

**in the above command we are trying to trigger an authentication to catch the ntlm hash then relay that has to make changes to the GPO

![[../../../attchments/Pasted image 20250404083815.png]]
using the above command we provided writeDacl perm to tthee studentx

![[../../../attchments/Pasted image 20250404084108.png]]
![[../../../attchments/Pasted image 20250404084123.png]]
![[../../../attchments/Pasted image 20250404084212.png]]

**we are making an directory std1-gp to start an rouge smbserver there and when gpoddity is run it creates the malicius template in GPT_Out so we are going to copy that and paste it in the std1-gp
share

![[../../../attchments/Pasted image 20250404084455.png]]
![[../../../attchments/Pasted image 20250404084526.png]]
we are granting everyone full control over the share


![[../../../attchments/Pasted image 20250404084633.png]]

in above now you can see the gpcfilesyspath has been changed

![[../../../attchments/Pasted image 20250404084748.png]]

