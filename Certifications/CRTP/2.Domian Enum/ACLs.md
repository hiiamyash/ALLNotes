
#active #windows #internalPentest 

![[../../../attchments/Pasted image 20250326204758.png]]

***So what is ACLs 

**lets suppose you are running an prosess that want to access any onter object in the ad enviroment than that process will provide an Access token that will contions the user sid and it;s creds and privilages that will be provided to the object then he will allow that process to run 

**when ever an process it trying to access an object the object have an list which is only allowed to acces that object that list is called is called *ACLs

![[../../../attchments/Pasted image 20250326205616.png]]
![[../../../attchments/Pasted image 20250326205816.png]]

**andrew is not allowed according to ACE 1 but Jane have write permission because she passes the ACE 2 ,Denial will always takes precedence



![[../../../attchments/Pasted image 20250326210704.png]]

![[../../../attchments/Pasted image 20250326212147.png]]

![[../../../attchments/Pasted image 20250327091751.png]]


![[../../../attchments/Pasted image 20250327091820.png]]

**the above is the command for FindingIntresting ACLs using powerview

![[../../../attchments/Pasted image 20250327091836.png]]

