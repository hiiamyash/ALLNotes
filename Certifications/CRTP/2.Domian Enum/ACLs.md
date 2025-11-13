
#active #windows #internalPentest 

![Pasted image 20250326204758](../../../attchments/Pasted%20image%2020250326204758.png)

***So what is ACLs 

**lets suppose you are running an prosess that want to access any onter object in the ad enviroment than that process will provide an Access token that will contions the user sid and it;s creds and privilages that will be provided to the object then he will allow that process to run 

**when ever an process it trying to access an object the object have an list which is only allowed to acces that object that list is called is called *ACLs

![Pasted image 20250326205616](../../../attchments/Pasted%20image%2020250326205616.png)
![Pasted image 20250326205816](../../../attchments/Pasted%20image%2020250326205816.png)

**andrew is not allowed according to ACE 1 but Jane have write permission because she passes the ACE 2 ,Denial will always takes precedence



![Pasted image 20250326210704](../../../attchments/Pasted%20image%2020250326210704.png)

![Pasted image 20250326212147](../../../attchments/Pasted%20image%2020250326212147.png)

![Pasted image 20250327091751](../../../attchments/Pasted%20image%2020250327091751.png)


![Pasted image 20250327091820](../../../attchments/Pasted%20image%2020250327091820.png)

**the above is the command for FindingIntresting ACLs using powerview

![Pasted image 20250327091836](../../../attchments/Pasted%20image%2020250327091836.png)

