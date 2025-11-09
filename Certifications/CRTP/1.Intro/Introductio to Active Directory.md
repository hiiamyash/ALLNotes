
#active #windows 

![[Pasted image 20250123173332.png]]

### **What is a Domain Controller (DC) and Active Directory (AD)?**

1. **Active Directory (AD):**
    
    - **Active Directory (AD)** is a **database and directory service** used by Windows networks to store and manage users, computers, and other network resources.
        
    - It **controls authentication and permissions** so that only authorized users can access certain resources.
        
2. **Domain Controller (DC):**
    
    - A **Domain Controller (DC)** is a **server that runs Active Directory** and is responsible for handling login requests, security policies, and authentication.
        
    - It **validates usernames and passwords** when users log in to the network.



![[Pasted image 20250123173400.png]]
![[Pasted image 20250123173538.png]]


`Schema` defines objects and their attribute for example You have an objectc called User so its's attributes will be it's passowrd ,accoount, phone number,  privlages etc.

`Query and index mechanism` helps us to search objects domains devices ect

where is the information about every object is stored it is stored in GC `Global Catalog`
and global Catalog is stored in the domain controllers

there can be multipple domain contrroller to scyn them we use `Replication Service`




### **Definition of Organizational Units (OUs) in Active Directory**

An **Organizational Unit (OU)** in **Active Directory (AD)** is a logical container used to organize and manage users, computers, and other AD objects within a domain. OUs help in applying **Group Policies** and delegating administrative control in a structured way.

---

### **Example: Understanding OUs Easily**

Imagine your company is like a **big office building**. Inside this building, different **departments** exist, such as:

- **HR (Human Resources)**
    
- **IT (Information Technology)**
    
- **Finance**
    

Each of these departments needs different security rules, access permissions, and policies. In **Active Directory**, you can create **Organizational Units (OUs)** for each department:

```scss
Company.com
│
├── HR (OU)
│   ├── Alice (User)
│   ├── Bob (User)
│   ├── HR-Computer1 (Computer)
│
├── IT (OU)
│   ├── Charlie (User)
│   ├── IT-Computer1 (Computer)
│   ├── IT-Server (Server)
│
├── Finance (OU)
│   ├── Dave (User)
│   ├── Finance-Computer1 (Computer)

```

![[Pasted image 20250123183028.png]]

if an domain in an forest is compramised then the enitre forest is compramised


## **Machines and Machines Account

Imagine your company has a bunch of computers. In a Windows domain, each of these computers gets its own special "ID card" and a secret password, just like employees do. This "ID card" is called a "machine account."

Here's a simpler breakdown:

Computers are like employees: Just like employees have user accounts, computers have machine accounts.
Machine accounts are for computers: These accounts let computers identify themselves to the network.
Special names: A computer named "Laptop1" will have a machine account named "Laptop1$


