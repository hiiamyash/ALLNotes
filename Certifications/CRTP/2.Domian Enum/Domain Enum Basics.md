#active #windows 


![Pasted image 20250219003206](Pasted%20image%2020250219003206.png)
![Pasted image 20250219003440](Pasted%20image%2020250219003440.png)
the darker one is for the powerview and lighter iss for the AD module
![Pasted image 20250219003824](Pasted%20image%2020250219003824.png)
**run the above to bypass the local inhanced login
https://github.com/OmerYa/Invisi-Shell/blob/master/RunWithRegistryNonAdmin.bat




![Pasted image 20250219003916](Pasted%20image%2020250219003916.png)
![Pasted image 20250219003954](Pasted%20image%2020250219003954.png)

![Pasted image 20250325234213](Pasted%20image%2020250325234213.png)

**above the moneycorp.local is the foresrr an dwe also know the domain controller

![Pasted image 20250325234323](Pasted%20image%2020250325234323.png)
***this will be used in glden ticket

![Pasted image 20250325234407](Pasted%20image%2020250325234407.png)

![Pasted image 20250325234600](Pasted%20image%2020250325234600.png)
**while forgging tickects in gilden ticket attck fist look at the kebros pilty before to avoid any type of detection

![Pasted image 20250325235041](Pasted%20image%2020250325235041.png)
**this will dump all ythe users  but it will too much information

![Pasted image 20250325235134](Pasted%20image%2020250325235134.png)
**the abive in way more good


![Pasted image 20250325235340](Pasted%20image%2020250325235340.png)
**why are we looking at the logon count beacuse we there is an domain admin account who has never loged in that means that is an decoy to trap us if we try to attack that then we will be caught

![Pasted image 20250326000457](Pasted%20image%2020250326000457.png)
**above will pull down the discription filed of an user this coulldd be an quick win beause peole can store intstiong this in that

![Pasted image 20250326000640](Pasted%20image%2020250326000640.png)
**above will give the computers Remember the domain admin can add 10 ou to the domain there is an chance that there can be decoy objects or computers that's why you need to check it's logon count

![Pasted image 20250326000937](Pasted%20image%2020250326000937.png)

![Pasted image 20250326001059](Pasted%20image%2020250326001059.png)
**abivee commad can hekp you find groups you are looking for

![Pasted image 20250326001352](Pasted%20image%2020250326001352.png)

![Pasted image 20250326001514](Pasted%20image%2020250326001514.png)
**This will help us to find members of the group domainadmins The built in Account Administratot can be identified using rid of 500 at the end

![Pasted image 20250326002600](Pasted%20image%2020250326002600.png)

![Pasted image 20250326002625](Pasted%20image%2020250326002625.png)

![Pasted image 20250326002725](Pasted%20image%2020250326002725.png)
![Pasted image 20250326002748](Pasted%20image%2020250326002748.png)







































```
Get-DomainUser -LDAPFilter "Description=*built*" | Select name,Description
```




