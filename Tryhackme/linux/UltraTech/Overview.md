![Exported image](../../../attchments/Exported%20image%2020241213213355-0.png)

nmap -p 21,22,8081 -sC -sV -A 10.10.30.86  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2024-09-05 16:07 IST  
Nmap scan report for 10.10.30.86  
Host is up (0.40s latency).
 
PORT STATE SERVICE VERSION  
21/tcp open ftp vsftpd 3.0.3  
22/tcp open ssh OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 2048 dc:66:89:85:e7:05:c2:a5:da:7f:01:20:3a:13:fc:27 (RSA)  
| 256 c3:67:dd:26:fa:0c:56:92:f3:5b:a0:b3:8d:6d:20:ab (ECDSA)  
|_ 256 11:9b:5a:d6:ff:2f:e4:49:d2:b5:17:36:0e:2f:1d:2f (ED25519)  
8081/tcp open http Node.js Express framework  
|_http-title: Site doesn't have a title (text/html; charset=utf-8).  
|_http-cors: HEAD GET POST PUT DELETE PATCH  
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 25.20 seconds

![Exported image](../../../attchments/Exported%20image%2020241213213357-1.png) ![Exported image](../../../attchments/Exported%20image%2020241213213359-2.png)  
![Exported image](../../../attchments/Exported%20image%2020241213213401-3.png)