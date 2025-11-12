
  

This room introduces commonly-used concepts, technologies, and security products that we need to be aware of.

In this room, the assumption is that we have already gained access to the machine, and we are ready to expand our knowledge more about the environment by performing enumerating for the following:

- Network infrastrucutre
- Active Directory Environment
- Users and Groups
- Host-based security solutions
- Network-based security solutions
- Applications and services



<h1>Network Infrastructure</h1>

Once arriving onto an unknown network, our first goal is to identify where we are and what we can get to. During the red team engagement, we need to understand what target system we are dealing with, what service the machine provides, what kind of network we are in

The Virtual Local Area Networks (VLANs) is a network technique used in network segmentation to control networking issues, such as broadcasting issues in the local network, and improve security. Hosts within the VLAN can only communicate with other hosts in the same VLAN network.

### Internal Networks

Internal Networks are subnetworks that are segmented and separated based on the importance of the internal device or the importance of the accessibility of its data.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/f86b9cce1276f4c317bcb4bae7686891.png)

The previous diagram is an example of the simple concept of network segmentation as the network is divided into two networks. The first one is for employee workstations and personal devices. The second is for private and internal network devices that provide internal services such as DNS, internal web, email services, etc.

**What happens if someone attacks?**

- If a hacker tries to break in, they’re stuck in the DMZ and can’t access your private data directly. It's like having a moat around your castle – they might reach the outer wall, but they can’t cross without extra effort.

### Network enumration


There are various things to check related to networking aspects such as TCP and UDP ports and established connections, routing tables, ARP tables, etc.

Let's start checking the target machine's TCP and UDP open ports. This can be done using the netstat command as shown below.

```
PS C:\Users\thm> netstat -na

Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    0.0.0.0:80             0.0.0.0:0              LISTENING
  TCP    0.0.0.0:88             0.0.0.0:0              LISTENING
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  TCP    0.0.0.0:389            0.0.0.0:0              LISTENING
```


Next, let's list the ARP table, which contains the IP address and the physical address of the computers that communicated with the target machines within the network. This could be helpful to see the communications within the network to scan the other machines for open ports and vulnerabilities.

```
PS C:\Users\thm> arp -a

Interface: 10.10.141.51 --- 0xa
  Internet Address      Physical Address      Type
  10.10.0.1             02-c8-85-b5-5a-aa     dynamic
  10.10.255.255         ff-ff-ff-ff-ff-ff     static
```



<h1>Active Directory (AD) environment</h1>

### What is the Active Directory (AD) environment?

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/a8e30315a65f3451771a2e038864fdee.png)
**Active Directory (AD)** is like a **school list** that keeps track of all the students (users), classrooms (computers), and rules (permissions). It helps the school (company) manage who can do what on the network.

It is a Windows-based directory service that stores and provides data objects to the internal network environment. It allows for centralized management of authentication and authorization. The AD contains essential information about the network and the environment, including users, computers, printers, etc. For example, AD might have users' details such as job title, phone number, address, passwords, groups, permission, etc.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/59664b98a3a0b01cf6b7e83e039ddb84.png)

The diagram is one possible example of how Active Directory can be designed. The AD controller is placed in a subnet for servers (shown above as server network), and then the AD clients are on a separate network where they can join the domain and use the AD services via the firewall.

The following is a list of Active Directory components that we need to be familiar with:

- Domain Controllers
- Organizational Units
- AD objects
- AD Domains
- Forest
- AD Service Accounts: Built-in local users, Domain users, Managed service accounts
- Domain Administrators

A **Domain Controller** is a Windows server that provides Active Directory services and controls the entire domain. It is a form of centralized user management that provides encryption of user data as well as controlling access to a network, including users, groups, policies, and computers. It also enables resource access and sharing. These are all reasons why attackers target a domain controller in a domain because it contains a lot of high-value information.

  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/c982e300552d540f0fc456cc05be21cd.png)


**Active Directory Objects** can be a single user or a group, or a hardware component, such as a computer or printer. Each domain holds a database that contains object identity information that creates an AD environment, including:

- Users - A security principal that is allowed to authenticate to machines in the domain
- Computers - A special type of user accounts
- GPOs - Collections of policies that are applied to other AD objects

***AD domains*** are a collection of Microsoft components within an AD network. 

***AD Forest*** is a collection of domains that trust each other. 

  
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/bb4bec81a78f745e8cbc38f7879002dd.png)


In order to check whether the Windows machine is part of the AD environment or not, one way, we can use the command prompt systeminfo command.

```
PS C:\Users\thm> systeminfo | findstr Domain
OS Configuration:          Primary Domain Controller
Domain:                    thmdomain.com
```

From the above output, we can see that the computer name is an AD with thmdomain.com as a domain name which confirms that it is a part of the AD environment. 

Note that if we get WORKGROUP in the domain section, then it means that this machine is part of a local workgroup.



<h1>Users and Groups Management</h1>

Gathering information about the compromised machine is essential that could be used in the next stage. Account discovery is the first step once we have gained initial access to the compromised machine to understand what we have and what other accounts are in the system.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/d981e1c73997b17ace78454c87b8a8c1.png)
An Active Directory environment contains various accounts with the necessary permissions, access, and roles for different purposes


- The built-in local users' accounts are used to manage the system locally, which is not part of the AD environment.
- Domain user accounts with access to an active directory environment can use the AD services (managed by AD).
- AD managed service accounts are limited domain user account with higher privileges to manage AD services.
- Domain Administrators are user accounts that can manage information in an Active Directory environment, including AD configurations, users, groups, permissions, roles, services, etc. One of the red team goals in engagement is to hunt for information that leads to a domain administrator having complete


![[Recording 20241221223322.m4a]]

The following are Active Directory Administrators accounts:

  

|                       |                                                            |
| --------------------- | ---------------------------------------------------------- |
| BUILTIN\Administrator | Local admin access on a domain controller                  |
| Domain Admins         | Administrative access to all resources in the domain       |
| Enterprise Admins     | Available only in the forest root                          |
| Schema Admins         | Capable of modifying domain/forest; useful for red teamers |
| Server Operators      | Can manage domain servers                                  |
| Account Operators     | Can manage users that are not in privileged groups         |

### Active Directory (AD) Enum

The following PowerShell command is to get all active directory user accounts. Note that we need to use  -Filter argument.

```
PS C:\Users\thm> Get-ADUser  -Filter *
DistinguishedName : CN=Administrator,CN=Users,DC=thmredteam,DC=com
Enabled           : True
GivenName         :
Name              : Administrator
ObjectClass       : user
ObjectGUID        : 4094d220-fb71-4de1-b5b2-ba18f6583c65
SamAccountName    : Administrator
SID               : S-1-5-21-1966530601-3185510712-10604624-500
Surname           :
UserPrincipalName :
PS C:\Users\thm>
```



The Distinguished Name (DN) is a collection of comma-separated key and value pairs used to identify unique records within the directory. The DN consists of Domain Component (DC), OrganizationalUnitName (OU), Common Name (CN), and others. The following "CN=User1,CN=Users,DC=thmredteam,DC=com" is an example of DN, which can be visualized as follow:  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/764c72d40ec3d823b05d6473702e00f5.png)

Using the SearchBase option, we specify a specific Common-Name CN in the active directory. For example, we can specify to list any user(s) that part of Users.


to find more users
```
PS C:\Users\thm> Get-ADUser -Filter * -SearchBase "CN=Users,DC=THMREDTEAM,DC=COM"


DistinguishedName : CN=Administrator,CN=Users,DC=thmredteam,DC=com
Enabled           : True
GivenName         :
Name              : Administrator
ObjectClass       : user
ObjectGUID        : 4094d220-fb71-4de1-b5b2-ba18f6583c65
SamAccountName    : Administrator
SID               : S-1-5-21-1966530601-3185510712-10604624-500
Surname           :
UserPrincipalName :
```




--------------------------------

# Host Security Solution #1


----------------Sceurity ON AN EDR

it is important to enumerate antivirus and security detection methods on an endpoint in order to stay as undetected as possible and reduce the chance of getting caught.

This task will discuss the common security solution used in corporate networks, divided into Host and Network security solutions.

## Host Security Solutions



![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/0e69d6b953d1c9c11d8581d31ea246d8.png)  

It is a set of software applications used to monitor and detect abnormal and malicious activities within the host, including:

1. Antivirus software  
    
2. Microsoft Windows Defender
3. Host-based Firewall
4. Security Event Logging and Monitoring   
    
5. Host-based Intrusion Detection System (HIDS)/ Host-based Intrusion Prevention System (HIPS)
6. Endpoint Detection and Response (EDR)

### Antivirus Software (AV)  

Antivirus software also known as anti-malware, is mainly used to monitor, detect, and prevent malicious software from being executed within the host

There are various detection techniques that the antivirus uses, including:

- Signature-based detection
- Heuristic-based detection
- Behavior-based detection


***Signature-based detection*** Often, researchers or users submit their infected files into an antivirus engine platform for further analysis by AV vendors, and if it confirms as malicious, then the signature gets registered in their database. The antivirus software compares the scanned file with a database of known signatures for possible attacks and malware on the client-side. If we have a match, then it considers a threat.

***Heuristic-based detection*** It scans and statically analyses in real-time in order to find suspicious properties in the application's code or check whether it uses uncommon Windows or system APIs. It does not rely on the signature-based attack in making the decisions, or sometimes it does. This depends on the implementation of the antivirus software.

***Behavior-based detection*** relies on monitoring and examining the execution of applications to find abnormal behaviors and uncommon activities, such as creating/updating values in registry keys, killing/creating processes, etc.



We can enumerate AV software using Windows built-in tools, such as wmic.

```
PS C:\Users\thm> wmic /namespace:\\root\securitycenter2 path antivirusproduct
```

This also can be done using PowerShell, which gives the same result

```
Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntivirusProduct
```

### Microsoft Windows Defender

Microsoft Windows Defender is a pre-installed antivirus security tool that runs on endpoints
MS Defender works in three protection modes: Active, Passive, Disable modes.

***Active*** mode is used where the MS Defender runs as the primary antivirus software on the machine where provides protection and remediation. ***Passive*** mode is run when a 3rd party antivirus software is installed. Therefore, it works as secondary antivirus software where it scans files and detects threats but does not provide remediation. Finally, ***Disable***  mode is when the MS Defender is disabled or uninstalled from the system.


We can use the following PowerShell command to **check** the service state of Windows Defender:

```
PS C:\Users\thm> Get-Service WinDefend

Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
```

```
PS C:\Users\thm> Get-MpComputerStatus | select RealTimeProtectionEnabled

RealTimeProtectionEnabled
-------------------------
                    False
```

As a result, MpComputerStatus highlights whether Windows Defender is enabled or not.



***Host-based Firewall***: It is a security tool installed and run on a host machine that can prevent and block attacker or red teamers' attack attempts. Thus, it is essential to enumerate and gather details about the firewall and its rules within the machine we have initial access to.  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/397c848fb415b72ce235915dea420900.png)  

The main purpose of the host-based firewall is to control the inbound and outbound traffic that goes through the device's interface. It protects the host from untrusted devices that are on the same network. A modern host-based firewall uses multiple levels of analyzing traffic, including packet analysis, while establishing the connection.

```
PS C:\Users\thm> Get-NetFirewallProfile | Format-Table Name, Enabled

Name    Enabled
----    -------
Domain     True
Private    True
Public     True
```

If we have admin privileges on the current user we logged in with, then we try to disable one or more than one firewall profile using the Set-NetFirewallProfile cmdlet.

```
PS C:\Windows\system32> Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled False
PS C:\Windows\system32> Get-NetFirewallProfile | Format-Table Name, Enabled
---- -------
Domain False
Private False
Public False
```

We can also learn and check the current Firewall rules, whether allowing or denying by the firewall.

```
PS C:\Users\thm> Get-NetFirewallRule | select DisplayName, Enabled, Description

```

we can take advantage of some PowerShell cmdlets such as Test-NetConnection and TcpClient. Assume we know that a firewall is in place, and we need to test inbound connection without extra tools, then we can do the following:

```
PS C:\Users\thm> Test-NetConnection -ComputerName 127.0.0.1 -Port 80


ComputerName     : 127.0.0.1
RemoteAddress    : 127.0.0.1
RemotePort       : 80
InterfaceAlias   : Loopback Pseudo-Interface 1
SourceAddress    : 127.0.0.1
TcpTestSucceeded : True

PS C:\Users\thm> (New-Object System.Net.Sockets.TcpClient("127.0.0.1", "80")).Connected
True
```

As a result, we can confirm the inbound connection on port 80 is open and allowed in the firewall. Note that we can also test for remote targets in the same network or domain names by specifying in the `-ComputerName argument` for the `Test-NetConnection`

```
 Get-NetFirewallRule | findstr "THM-Connection"
```






# Host Security Solution #2


##  Security Event Logging and Monitoring

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/980c1573a3ec3d309d0f2360c16b019a.png)

By default, Operating systems log various activity events in the system using log files. The event logging feature is available to the IT system and network administrators to monitor and analyze important events, whether on the host or the network side. In cooperating networks, security teams utilize the logging event technique to track and investigate security incidents.

We can get a list of available event logs on the local machine using the `Get-EventLog cmdlet.`

```
PS C:\Users\thm> Get-EventLog -List

  Max(K) Retain OverflowAction        Entries Log
  ------ ------ --------------        ------- ---
     512      7 OverwriteOlder             59 Active Directory Web Services
  20,480      0 OverwriteAsNeeded         512 Application
     512      0 OverwriteAsNeeded         170 Directory Service
 102,400      0 OverwriteAsNeeded          67 DNS Server
  20,480      0 OverwriteAsNeeded       4,345 System
  15,360      0 OverwriteAsNeeded       1,692 Windows PowerShell
```

Sometimes, the list of available event logs gives you an insight into what applications and services are installed on the machine! For example, we can see that the local machine has Active Directory, DNS server, etc




## System Monitor (Sysmon)

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/8c77acd6d831c3b9f4c5b5f0cdc0d08c.png)  

The sysmon tool is not an essential tool (not installed by default), but it starts gathering and logging events once installed. These logs indicators can significantly help system administrators and blue teamers to track and investigate malicious activity and help with general troubleshooting.



One of the great features of the sysmon  tool is that it can log many important events, and you can also create your own rule(s) and configuration to monitor:

- Process creation and termination
- Network connections
- Modification on file
- Remote threats
- Process and memory access
- and many others

we need to avoid sysmon as red teamers ,first we need to find out weather sysmon is there or not
We can look for a process or service that has been named "Sysmon" within the current process or services as follows,
```
PS C:\Users\thm> Get-Process | Where-Object { $_.ProcessName -eq "Sysmon" }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    373      15    20212      31716              3316   0 Sysmon
```

or look for services as follows,

```
PS C:\Users\thm> Get-CimInstance win32_service -Filter "Description = 'System Monitor service'" 
# or 
Get-Service | where-object {$_.DisplayName -like "*sysm*"}
```

It also can be done by checking the Windows registry

```
PS C:\Users\thm> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WINEVT\Channels\Microsoft-Windows-Sysmon/Operational
```

All these commands confirm if the sysmon tool is installed. Once we detect it, we can try to find the sysmon configuration file if we have readable permission to understand what system administrators are monitoring.

thiss command is to find the configratiion file 

```
PS C:\Users\thm> findstr /si '<ProcessCreate onmatch="exclude">' C:\tools\*
C:\tools\Sysmon\sysmonconfig.xml:      
C:\tools\Sysmon\sysmonconfig.xml:      
```

there is an tryhackme room about sysmon 



## Host-based Intrusion Detection/Prevention System (HIDS/HIPS)

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/933d57959af6b3ac9396e688698bb358.png)

**HIDS** stands for Host-based Intrusion Detection System, 

It is software that has the ability to monitor and detect abnormal and malicious activities in a host. The primary purpose of HIDS is to detect suspicious activities and `not to prevent them`. There are two methods that the host-based or network intrusion detection system works, including:

- Signature-based IDS - it looks at checksums and message authentication.
- Anomaly-based IDS looks for unexpected activities, including abnormal bandwidth usage, protocols, and ports.

Host-based Intrusion Prevention Systems (**HIPS**)

It is a detection and prevention solution against well-known attacks and abnormal behaviours. HIPS can audit the host's log files, monitor processes, and protect system resources. HIPS combines many product features such as antivirus, behaviour analysis, network, application firewall, etc.


## Endpoint Detection and Response (EDR)

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/92a60622a80d64cc6dbedaa6c207662b.png)

It is also known as Endpoint Detection and Threat Response (EDTR)



The EDR is a cybersecurity solution that defends against malware and other threats. EDRs can look for malicious files, monitor endpoint, system, and network events, and record them in a database for further analysis, detection, and investigation. EDRs are the next generation of antivirus and detect malicious activities on the host in real-time


EDR analyze system data and behavior for making section threats, including

- Malware, including viruses, trojans, adware, keyloggers
- Exploit chains
- Ransomware

Below are some common EDR software for endpoints

- Cylance
- Crowdstrike
- Symantec
- SentinelOne
- Many others

Even though an attacker successfully delivered their payload and bypassed EDR in receiving reverse shell, EDR is still running and monitors the system. It may block us from doing something else if it flags an alert

We can use scripts for enumerating security products within the machine, such as [Invoke-EDRChecker](https://github.com/PwnDexter/Invoke-EDRChecker) and [SharpEDRChecker](https://github.com/PwnDexter/SharpEDRChecker). They check for commonly used Antivirus, EDR



# Network Security Solutions


## Network Security Solutions

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/e11f81fc50e049855849e20d7f34e453.png)  

Network security solutions could be software or hardware appliances used to monitor, detect and prevent malicious activities within the network. It focuses on protecting clients and devices connected to the cooperation network. The network security solution includes but is not limited to:

- Network Firewall
- SIEM
- IDS/IPS

## Network Firewall

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/e4a1c6568d8f21c9f0fb0ea8c193a880.png)  

A firewall is the first checkpoint for untrusted traffic that arrives at a network. The firewall filters the untrusted traffic before passing it into the network based on rules and policies

The following are some firewall types that enterprises may use.

- Packet-filtering firewalls
- Proxy firewalls
- NAT firewalls
- Web application firewalls



## Security Information and Event Management (SIEM)

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/4a5624e396e6075fc18eae92f9d3d84e.png)

SIEM combines Security Information Management (SIM) and Security Event Management (SEM) to monitor and analyze events and track and log data in real-time. SIEM helps system administrators and blue teamers to monitor and track potential security threats and vulnerabilities before causing damage to an organization.



IEM is capable of detecting advanced and unknown threats using integrated threat intelligence and AI technologies, including Insider threats, security vulnerabilities, phishing attacks, Web attacks, DDoS attacks, data exfiltration, etc.

The following are some of the SIEM products that are commonly seen in many enterprises:

- Splunk
- LogRhythm NextGen SIEM Platform
- SolarWinds Security Event Manager
- Datadog Security Monitoring
- many others


They both read network packets looking for abnormal behaviors and known threats pre-loaded into a previous database. The significant difference between both solutions is that the IDS requires human interaction or 3rd party software to analyze the data to take action. The IPS is a control system that accepts or rejects packets based on policies and rules.

The following are common enterprise IDS/IPS products 

- Palo Alto Networks
- Cisco's Next-Generation 
- McAfee Network Security Platform (NSP)
- Trend Micro TippingPoint
- Suricata


# Applications and Services

This task will expand our knowledge needed to learn more about the system. We discussed account discovery and security products within the system in previous tasks. We will continue learning more about the system, including:

- Installed applications  
    
- Services and processes
- Sharing files and printers  
    
- Internal services: DNS and local web applications

## Installed Applications

First, we start enumerating the system for installed applications by checking the application's name and version. As a red teamer, this information will benefit us. We may find vulnerable software installed to exploit and escalate our system privileges


 We will be using the wmic Windows command to list all installed applications and their version.

```
PS C:\Users\thm> wmic product get name,version
Name                                                            Version
Microsoft Visual C++ 2019 X64 Minimum Runtime - 14.28.29910     14.28.29910
AWS Tools for Windows                                           3.15.1248
Amazon SSM Agent                                                3.0.529.0
aws-cfn-bootstrap                                               2.0.5
AWS PV Drivers                                                  8.3.4
Microsoft Visual C++ 2019 X64 Additional Runtime - 14.28.29910  14.28.29910

```

Another interesting thing is to look for particular text strings, hidden directories, backup files. Then we can use the PowerShell cmdlets, Get-ChildItem, as follow:

```
PS C:\Users\thm> Get-ChildItem -Hidden -Path C:\Users\kkidd\Desktop\
```



## Services and Process

Sometimes Windows services have misconfiguration permissions, which escalates the current user access level of permissions. Therefore, we must look at running services and perform services and processes reconnaissance

For example, the compromised system may have a custom client application used for internal purposes. Custom internally developed software is the most common root cause of escalation vectors. Thus, it is worth digging more to get details about the current process.


## Sharing files and Printers

Sharing files and network resources is commonly used in personal and enterprise environments. System administrators misconfigure access permissions, and they may have useful information about other accounts and systems. For more information on printer hacking, we suggest trying out the following TryHackMe room: [Printer Hacking 101](https://tryhackme.com/room/printerhacking101).

## Internal services: DNS, local web applications, etc

The following are some of the internal services that are commonly used that we are interested in:

- DNS Services
- Email Services
- Network File Share
- Web application
- Database service



Let's try listing the running services using the Windows command prompt net start to check if there are any interesting running services


```
PS C:\Users\thm> net start
These Windows services are started:

Active Directory Web Services
Amazon SSM Agent
Application Host Helper Service
Cryptographic Services
DCOM Server Process Launcher
DFS Namespace
DFS Replication
DHCP Client
Diagnostic Policy Service
THM Demo
DNS Client
```

now in the above results lets suppose we want to know about THM Demo
then

```
PS C:\Users\thm> wmic service where "name like 'THM Demo'" get Name,PathName
Name         PathName
THM Service  c:\Windows\thm-demo.exe
```

We find the file name and its path; now let's find more details using the `Get-Process` cmdlet

```
PS C:\Users\thm> Get-Process -Name thm-demo

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
82       9    13128       6200              3212   0 thm-service
```

Once we find its process ID, let's check if providing a network service by listing the listening ports within the system

```
PS C:\Users\thm> netstat -noa |findstr "LISTENING" |findstr "3212"   TCP    0.0.0.0:8080          0.0.0.0:0              LISTENING       3212   TCP    [::]:8080             [::]:0                 LISTENING       3212
```



We mentioned that DNS service is a commonly used protocol in any active directory environment and network. The attached machine provides DNS services for AD. Let's enumerate the DNS by performing a zone transfer DNS and see if we can list all records.


We will perform DNS zone transfer using the Microsoft tool is nslookup.exe.

```
PS C:\Users\thm> nslookup.exe
Default Server:  UnKnown
Address:  ::1
```

Once we execute it, we provide the DNS server that we need to ask, which in this case is the target machine

```
> server 10.10.216.235
Default Server:  [10.10.216.235]
Address:  10.10.216.235
```

Now let's try the DNS zone transfer on the domain we find in the AD environment.

```
> ls -d thmredteam.com
[[10.10.216.235]]
 thmredteam.com.                SOA    ad.thmredteam.com hostmaster.thmredteam.com. (732 900 600 86400 3600)
 thmredteam.com.                A      10.10.216.235
 thmredteam.com.                NS     ad.thmredteam.com
***
 ad                             A      10.10.216.235
```

The previous output is an example of successfully performing the DNS zone transfer.

