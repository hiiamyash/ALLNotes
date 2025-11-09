nmap -p 80,135,139,445,3389,8080,49152,49153,49154,49155,49157,49165 -A -T4 mountain.thm  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2024-11-30 21:14 IST  
Nmap scan report for mountain.thm (10.10.185.229)  
Host is up (0.42s latency).
 
PORT STATE SERVICE VERSION  
80/tcp open http Microsoft IIS httpd 8.5  
|_http-server-header: Microsoft-IIS/8.5  
|_http-title: Site doesn't have a title (text/html).  
| http-methods:  
|_ Potentially risky methods: TRACE  
135/tcp open msrpc Microsoft Windows RPC  
139/tcp open netbios-ssn Microsoft Windows netbios-ssn  
445/tcp open microsoft-ds Microsoft Windows Server 2008 R2 - 2012 microsoft-ds  
3389/tcp open ssl/ms-wbt-server?  
|_ssl-date: 2024-11-30T15:46:46+00:00; +2s from scanner time.  
| rdp-ntlm-info:  
| Target_Name: STEELMOUNTAIN  
| NetBIOS_Domain_Name: STEELMOUNTAIN  
| NetBIOS_Computer_Name: STEELMOUNTAIN  
| DNS_Domain_Name: steelmountain  
| DNS_Computer_Name: steelmountain  
| Product_Version: 6.3.9600  
|_ System_Time: 2024-11-30T15:46:39+00:00  
| ssl-cert: Subject: commonName=steelmountain  
| Not valid before: 2024-11-29T15:39:25  
|_Not valid after: 2025-05-31T15:39:25  
8080/tcp open http HttpFileServer httpd 2.3  
|_http-server-header: HFS 2.3  
|_http-title: HFS /  
49152/tcp open msrpc Microsoft Windows RPC  
49153/tcp open msrpc Microsoft Windows RPC  
49154/tcp open msrpc Microsoft Windows RPC  
49155/tcp open msrpc Microsoft Windows RPC  
49157/tcp open msrpc Microsoft Windows RPC  
49165/tcp open msrpc Microsoft Windows RPC  
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port  
Aggressive OS guesses: Microsoft Windows Server 2012 (96%), Microsoft Windows Server 2012 R2 (96%), Microsoft Windows Server 2012 R2 Update 1 (96%), Microsoft Windows 7, Windows Server 2012, or Windows 8.1 Update 1 (96%), Microsoft Windows Vista SP1 (96%), Microsoft Windows Server 2012 or Server 2012 R2 (95%), Microsoft Windows Server 2008 SP2 Datacenter Version (94%), Microsoft Windows 7 or Windows Server 2008 R2 (94%), Microsoft Windows Server 2008 R2 (94%), Microsoft Windows Home Server 2011 (Windows Server 2008 R2) (93%)  
No exact OS matches for host (test conditions non-ideal).  
Network Distance: 4 hops  
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows
    
---------------------- order  
first 80  
then 8080 got initial acces  
then smb 139 ans 445