![[../../../attchments/Exported image 20241213185456-0.png|Exported image]]

nmap -p 22,80 -sC -sV -A rootme.thm  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2024-09-05 14:45 IST  
Nmap scan report for rootme.thm (10.10.30.89)  
Host is up (0.41s latency).
 
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 2048 4a:b9:16:08:84:c2:54:48:ba:5c:fd:3f:22:5f:22:14 (RSA)  
| 256 a9:a6:86:e8:ec:96:c3:f0:03:cd:16:d5:49:73:d0:82 (ECDSA)  
|_ 256 22:f6:b5:a6:54:d9:78:7c:26:03:5a:95:f3:f9:df:cd (ED25519)  
80/tcp open http Apache httpd 2.4.29 ((Ubuntu))  
|_http-server-header: Apache/2.4.29 (Ubuntu)  
| http-cookie-flags:  
| /:  
| PHPSESSID:  
|_ httponly flag not set  
|_http-title: HackIT - Home  
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port  
Aggressive OS guesses: Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (95%), ASUS RT-N56U WAP (Linux 3.4) (93%), Linux 3.16 (93%), Linux 2.6.32 (93%), Linux 2.6.39 - 3.2 (93%), Linux 3.1 - 3.2 (93%), Linux 3.11 (93%), Linux 3.2 - 4.9 (93%)  
No exact OS matches for host (test conditions non-ideal).  
Network Distance: 4 hops  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
TRACEROUTE (using port 443/tcp)  
HOP RTT ADDRESS  
1 274.35 ms 10.2.0.1  
2 ... 3  
4 404.38 ms rootme.thm (10.10.30.89)
 
OS and Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 31.43 seconds