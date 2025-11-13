![Exported image](../../../attchments/Exported%20image%2020241213184210-0.png)  

nmap -p 22,80 -A -T4 10.10.10.242  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2024-11-13 23:00 IST  
Nmap scan report for 10.10.10.242  
Host is up (0.096s latency).
 
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 3072 be:54:9c:a3:67:c3:15:c3:64:71:7f:6a:53:4a:4c:21 (RSA)  
| 256 bf:8a:3f:d4:06:e9:2e:87:4e:c9:7e:ab:22:0e:c0:ee (ECDSA)  
|_ 256 1a:de:a1:cc:37:ce:53:bb:1b:fb:2b:0b:ad:b3:f6:84 (ED25519)  
80/tcp open http Apache httpd 2.4.41 ((Ubuntu))  
|_http-server-header: Apache/2.4.41 (Ubuntu)  
|_http-title: Emergent Medical Idea  
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
 
-----------let the scans run then turn on burpsuit and look at the website  
-------If you see a /usr/bin/pkexec in suid then always check for gcc