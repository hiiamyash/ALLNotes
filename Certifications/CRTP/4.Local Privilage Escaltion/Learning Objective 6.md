#active 
#windows
![Pasted image 20250404081655](../../../attchments/Pasted%20image%2020250404081655.png)

![Pasted image 20250404081801](../../../attchments/Pasted%20image%2020250404081801.png)

gpcfilesyspath is the policy we are going to modify

![Pasted image 20250404081903](../../../attchments/Pasted%20image%2020250404081903.png)

you can see that the Devops user that has writeDacl perm on the Devopsgroup policy

![Pasted image 20250404082756](../../../attchments/Pasted%20image%2020250404082756.png)

-t ldaps:ip 

the ip is of the doamin controller

and -wh ip is the ipp of our w=machine

![Pasted image 20250404083229](../../../attchments/Pasted%20image%2020250404083229.png)

![Pasted image 20250404083240](../../../attchments/Pasted%20image%2020250404083240.png)

make this powershell command as the shortcut

![Pasted image 20250404083411](../../../attchments/Pasted%20image%2020250404083411.png)

this is the shortcut we created
now we will copy this to the dc-cropci//AI share

![Pasted image 20250404083624](../../../attchments/Pasted%20image%2020250404083624.png)

**in the above command we are trying to trigger an authentication to catch the ntlm hash then relay that has to make changes to the GPO

![Pasted image 20250404083815](../../../attchments/Pasted%20image%2020250404083815.png)
using the above command we provided writeDacl perm to tthee studentx

![Pasted image 20250404084108](../../../attchments/Pasted%20image%2020250404084108.png)
![Pasted image 20250404084123](../../../attchments/Pasted%20image%2020250404084123.png)
![Pasted image 20250404084212](../../../attchments/Pasted%20image%2020250404084212.png)

**we are making an directory std1-gp to start an rouge smbserver there and when gpoddity is run it creates the malicius template in GPT_Out so we are going to copy that and paste it in the std1-gp
share

![Pasted image 20250404084455](../../../attchments/Pasted%20image%2020250404084455.png)
![Pasted image 20250404084526](../../../attchments/Pasted%20image%2020250404084526.png)
we are granting everyone full control over the share


![Pasted image 20250404084633](../../../attchments/Pasted%20image%2020250404084633.png)

in above now you can see the gpcfilesyspath has been changed

![Pasted image 20250404084748](../../../attchments/Pasted%20image%2020250404084748.png)

