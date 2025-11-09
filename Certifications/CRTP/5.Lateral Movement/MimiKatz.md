#active 
#windows
![[Pasted image 20250407090553.png]]

![[Pasted image 20250407095921.png]]

Runs SafetyKatz beacuse mimikatz can be easily detected


What is NTDS.dit

The NTDS.DIT file is a crucial component of Microsoft's Active Directory Domain Services (AD DS), serving as the primary database file that stores and organizes all the information related to objects in the domain, including users, groups, computers, and more.24 It houses critical data such as user account details, passwords, group memberships, and other object attributes.




![[Pasted image 20250407101216.png]]

Difference Between Over pass the hash and Pass the hash is that Over-pass the hash will compramise the Domain users and Pass the hash will compromise the local users

### 🎭 **Pass-the-Hash (PtH)** – The Classic Impersonator

- **What it is:** You steal a user's **NTLM hash** (like a fingerprint of their password) and use it **as-is** to authenticate yourself on another system **without ever needing the plaintext password**.
### **Over-Pass-the-Hash (OPtH)** – The Smart Bypass

- **What it is:** Instead of using the hash directly for access, you **create a Kerberos ticket** using the stolen hash and then **use that ticket** to access services.



## 💻 **Local User Example**

- You're on `Workstation-01`.
    
- You compromise a local user like `jdoe`.
    
- That user exists **only on Workstation-01**.
    
- If you move to `Workstation-02`, `jdoe` **won’t exist** there unless manually created.
    

---

## 🏢 **Domain User Example**

- You compromise `corp\jsmith` (a domain account).
    
- That user is centrally stored in AD (e.g., `DC01.corp.local`).
    
- That same account can potentially log into **multiple systems** (depending on permissions).
    
- Perfect for **pivoting** across the environment.


![[Pasted image 20250407101756.png]]

performing OPTH using safteykatz.exe you need Administrative cmd but using Rubeus you can perform OPTH without the administrative cmd



![[Pasted image 20250407102009.png]]
above command can be used to get kerbrobe tokens

