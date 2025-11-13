![[../../../attchments/Exported image 20241213184550-0.png|Exported image]]

PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.4p1 Debian 10+deb9u1 (protocol 2.0)  
| ssh-hostkey:  
| 2048 77:00:84:f5:78:b9:c7:d3:54:cf:71:2e:0d:52:6d:8b (RSA)  
| 256 78:b8:3a:f6:60:19:06:91:f5:53:92:1d:3f:48:ed:53 (ECDSA)  
|_ 256 e4:45:e9:ed:07:4d:73:69:43:5a:12:70:9d:c4:af:76 (ED25519)  
25/tcp open smtp JAMES smtpd 2.3.2  
|_smtp-commands: solidstate Hello nmap.scanme.org (10.10.14.11 [10.10.14.11])  
80/tcp open http Apache httpd 2.4.25 ((Debian))  
|_http-server-header: Apache/2.4.25 (Debian)  
|_http-title: Home - Solid State Security  
110/tcp open pop3 JAMES pop3d 2.3.2  
4555/tcp open rsip?  
| fingerprint-strings:  
| GenericLines:  
| JAMES Remote Administration Tool 2.3.2  
| Please enter your login and password  
| Login id:  
| Password:  
| Login failed for  
|_ Login id:  
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [https://nmap.org/cgi-bin/submit.cgi?new-service](https://nmap.org/cgi-bin/submit.cgi?new-service) :  
SF-Port4555-TCP:V=7.94SVN%I=7%D=11/11%Time=6731900D%P=x86_64-pc-linux-gnu%  
SF:r(GenericLines,7C,"JAMES\x20Remote\x20Administration\x20Tool\x202\.3\.2  
SF:\nPlease\x20enter\x20your\x20login\x20and\x20password\nLogin\x20id:\nPa  
SF:ssword:\nLogin\x20failed\x20for\x20\nLogin\x20id:\n");  
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port  
Aggressive OS guesses: Linux 3.12 (95%), Linux 3.13 (95%), Linux 3.16 (95%), Linux 3.2 - 4.9 (95%), Linux 4.4 (95%), Linux 4.8 (95%), Linux 4.9 (95%), Linux 3.18 (95%), Linux 3.8 - 3.11 (95%), Linux 4.2 (95%)  
No exact OS matches for host (test conditions non-ideal).  
Network Distance: 2 hops  
Service Info: Host: solidstate; OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
TRACEROUTE (using port 80/tcp)  
HOP RTT ADDRESS  
1 440.21 ms 10.10.14.1  
2 440.41 ms 10.10.10.51
    ![[../../../attchments/Exported image 20241213184553-1.png|Exported image]]   
------------------------CREDS  
username: mindy  
pass: P@55W0rd1!2@