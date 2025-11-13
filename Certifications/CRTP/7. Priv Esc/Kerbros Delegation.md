
![[../../../attchments/Pasted image 20250627173222.png]]

![[../../../attchments/Pasted image 20250627173234.png]]
![[../../../attchments/Pasted image 20250627173208.png]]

![[../../../attchments/Pasted image 20250627173444.png]]

![[../../../attchments/Pasted image 20250627175018.png]]


# Steps to abuse

**FInd find the users that has uncontsained delegation enabled

![[../../../attchments/Pasted image 20250627175427.png]]

![[../../../attchments/Pasted image 20250627175501.png]]

![[../../../attchments/Pasted image 20250627175649.png]]

you can force server2 to connect to the server 1

![[../../../attchments/Pasted image 20250627175809.png]]

![[../../../attchments/Pasted image 20250627175817.png]]


### Kerberos Delegation (in general)

Think of it as giving someone your ID badge temporarily so they can access a resource **on your behalf**—but only within a trusted network. It's how services in a Windows domain can impersonate users securely.

---

### 🎭 1. **Unconstrained Delegation**

- **How it works:** A service can impersonate **any user** to access **any service** after they authenticate.
    
- **Risky?** Oh yeah. If an attacker compromises that service, they can become **anyone** in the domain. It's like handing them your all-access pass.
    
- **Red Team Use:** Target services with this setup to impersonate domain admins—classic "Golden Ticket" play.
    

---

### 🔒 2. **Constrained Delegation**

- **How it works:** You can only impersonate users **to specific services** you've been allowed to access.
    
- **More secure:** Limits abuse potential because the list of services is controlled.
    
- **Red Team Tip:** Abuse it with tools like **Rubeus** for S4U2Self + S4U2Proxy chain impersonation.
    

---

### 🎯 3. **Resource-Based Constrained Delegation (RBCD)**

- **How it works:** Like Constrained Delegation, but **the target (resource)** decides **who can impersonate to it**.
    
- **Why cool?** Delegation is set by the target, so attackers can configure it if they control a machine account.
    
- **Red Team Favorite:** Combine with machine account creation and `Set-ADComputer` for juicy lateral movement.
    

---

### TL;DR Cheat Sheet:

| Type          | Who controls?                    | Risk Level | Use Case                         |
| ------------- | -------------------------------- | ---------- | -------------------------------- |
| Unconstrained | Service's own config             | 🔥🔥🔥     | Full impersonation (risky)       |
| Constrained   | Admin sets allowed targets       | 🔒         | Impersonate to specific services |
| RBCD          | Target controls who can delegate | 🧠🔓       | Great for lateral movement       |