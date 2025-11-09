nmap -p 53,88,389,445,464,139,135,593,636,1433,3268,3269,5985,9389,49667,49689,49690,49732,49715,49751 -A -T4 10.10.11.202  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2024-11-18 04:34 EST  
Stats: 0:01:52 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan  
NSE Timing: About 95.00% done; ETC: 04:36 (0:00:00 remaining)  
Nmap scan report for escape.htb (10.10.11.202)  
Host is up (0.43s latency).
 
PORT STATE SERVICE VERSION  
53/tcp open domain Simple DNS Plus  
88/tcp open kerberos-sec Microsoft Windows Kerberos (server time: 2024-11-18 17:21:47Z)  
135/tcp open msrpc Microsoft Windows RPC  
139/tcp open netbios-ssn Microsoft Windows netbios-ssn  
389/tcp open ldap Microsoft Windows Active Directory LDAP (Domain: sequel.htb0., Site: Default-First-Site-Name)  
|_ssl-date: 2024-11-18T17:23:31+00:00; +7h46m47s from scanner time.  
| ssl-cert: Subject: commonName=dc.sequel.htb  
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:dc.sequel.htb  
| Not valid before: 2024-11-17T03:01:01  
|_Not valid after: 2025-11-17T03:01:01  
445/tcp open microsoft-ds?  
464/tcp open kpasswd5?  
593/tcp open ncacn_http Microsoft Windows RPC over HTTP 1.0  
636/tcp open ssl/ldap Microsoft Windows Active Directory LDAP (Domain: sequel.htb0., Site: Default-First-Site-Name)  
| ssl-cert: Subject: commonName=dc.sequel.htb  
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:dc.sequel.htb  
| Not valid before: 2024-11-17T03:01:01  
|_Not valid after: 2025-11-17T03:01:01  
|_ssl-date: 2024-11-18T17:23:30+00:00; +7h46m47s from scanner time.  
1433/tcp open ms-sql-s Microsoft SQL Server 2019 15.00.2000.00; RTM  
| ms-sql-ntlm-info:  
| 10.10.11.202:1433:  
| Target_Name: sequel  
| NetBIOS_Domain_Name: sequel  
| NetBIOS_Computer_Name: DC  
| DNS_Domain_Name: sequel.htb  
| DNS_Computer_Name: dc.sequel.htb  
| DNS_Tree_Name: sequel.htb  
|_ Product_Version: 10.0.17763  
|_ssl-date: 2024-11-18T17:23:31+00:00; +7h46m47s from scanner time.  
| ms-sql-info:  
| 10.10.11.202:1433:  
| Version:  
| name: Microsoft SQL Server 2019 RTM  
| number: 15.00.2000.00  
| Product: Microsoft SQL Server 2019  
| Service pack level: RTM  
| Post-SP patches applied: false  
|_ TCP port: 1433  
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback  
| Not valid before: 2024-11-16T19:11:21  
|_Not valid after: 2054-11-16T19:11:21  
3268/tcp open ldap Microsoft Windows Active Directory LDAP (Domain: sequel.htb0., Site: Default-First-Site-Name)  
| ssl-cert: Subject: commonName=dc.sequel.htb  
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:dc.sequel.htb  
| Not valid before: 2024-11-17T03:01:01  
|_Not valid after: 2025-11-17T03:01:01  
|_ssl-date: 2024-11-18T17:23:31+00:00; +7h46m47s from scanner time.  
3269/tcp open ssl/ldap Microsoft Windows Active Directory LDAP (Domain: sequel.htb0., Site: Default-First-Site-Name)  
| ssl-cert: Subject: commonName=dc.sequel.htb  
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:dc.sequel.htb  
| Not valid before: 2024-11-17T03:01:01  
|_Not valid after: 2025-11-17T03:01:01  
|_ssl-date: 2024-11-18T17:23:30+00:00; +7h46m47s from scanner time.  
5985/tcp open http Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)  
|_http-title: Not Found  
|_http-server-header: Microsoft-HTTPAPI/2.0  
9389/tcp open mc-nmf .NET Message Framing  
49667/tcp open msrpc Microsoft Windows RPC  
49689/tcp open ncacn_http Microsoft Windows RPC over HTTP 1.0  
49690/tcp open msrpc Microsoft Windows RPC  
49715/tcp open msrpc Microsoft Windows RPC  
49732/tcp open msrpc Microsoft Windows RPC  
49751/tcp open msrpc Microsoft Windows RPC
 
-------smb version