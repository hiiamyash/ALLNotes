 #windows #active #internalPentest 

![[../../../attchments/Pasted image 20250402152232.png]]
![[../../../attchments/Pasted image 20250402152250.png]]
![[../../../attchments/Pasted image 20250402152325.png]]
**the abov image says that if "A" has an Bidirection trust with "B" and "B" also has a directionl trust with "C" then Practically A and C have bidirection trust

IF A = B = C then A = C


Transitive Trust is the intra forest trust like the parent child and root domain and other domain

Non-Transitive Trust are 



![[../../../attchments/Pasted image 20250402155747.png]]

**the above is the default or the automatic trusts 

![[../../../attchments/Pasted image 20250402161511.png]]

![[../../../attchments/Pasted image 20250402162308.png]]

![[../../../attchments/Pasted image 20250402162906.png]]


![[../../../attchments/Pasted image 20250402163614.png]]

**in the above bloodhound image you can see the trusts eurocorp.local is an tree root domain trust moneycorp.local and dollarcorp.moneycorp.local is an parent trust and us.dollarcor.moneycorp.local is an child trust


![[../../../attchments/Pasted image 20250402163836.png]]

![[../../../attchments/Pasted image 20250402163906.png]]

trustattribute for lastone is FILTER_SIDS that means it is an external trust


![[../../../attchments/Pasted image 20250402164050.png]]

![[../../../attchments/Pasted image 20250402164108.png]]



