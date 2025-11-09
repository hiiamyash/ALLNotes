#windows
#active 


![Pasted image 20250403204432](Pasted%20image%2020250403204432.png)

![Pasted image 20250403204507](/ALLNotes/attchments/Pasted%20image%2020250403204507.png)


![Pasted image 20250403204532](Pasted%20image%2020250403204532.png)


![Pasted image 20250403205113](Pasted%20image%2020250403205113.png)

**Explaination of GOPddity Attack In my Words

So what we are going to do is We are going to NTML relay the credentials of an User who  has writeDacl permision on the GPO then we are going to modify gPCFileSysPath tell it to point to an Malicous Group Policy that is going to an Malicious Template we Created  



![Pasted image 20250403213048](Pasted%20image%2020250403213048.png)

**using malicious Shortcut we are going to trigger authenticaiton hence relatying the Creds of the user whoo has writeDacl perm to modify the aPCFileSysPath to an smb share were we have perm to host our malicous template (GPT) Group Policy Template


![Pasted image 20250403214233](Pasted%20image%2020250403214233.png)

