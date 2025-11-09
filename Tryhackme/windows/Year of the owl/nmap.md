

┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/windows/yearoftheowl]
└─$ nmap -p 139,3306,80,3389,445,443 -A -T4 10.10.193.121
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-12-19 14:35 IST
Nmap scan report for 10.10.193.121
Host is up (0.46s latency).

PORT     STATE SERVICE       VERSION
80/tcp   open  http          Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.10)
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.10
|_http-title: Year of the Owl
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
443/tcp  open  ssl/http      Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.10)
| tls-alpn: 
|_  http/1.1
|_ssl-date: TLS randomness does not represent time
|_http-title: Year of the Owl
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.10
| ssl-cert: Subject: commonName=localhost
| Not valid before: 2009-11-10T23:48:47
|_Not valid after:  2019-11-08T23:48:47
445/tcp  open  microsoft-ds?
3306/tcp open  mysql?
| fingerprint-strings: 
|   NULL: 
|_    Host 'ip-10-13-74-171.eu-west-1.compute.internal' is not allowed to connect to this MariaDB server
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: YEAR-OF-THE-OWL
|   NetBIOS_Domain_Name: YEAR-OF-THE-OWL
|   NetBIOS_Computer_Name: YEAR-OF-THE-OWL
|   DNS_Domain_Name: year-of-the-owl
|   DNS_Computer_Name: year-of-the-owl
|   Product_Version: 10.0.17763
|_  System_Time: 2024-12-19T09:06:40+00:00
| ssl-cert: Subject: commonName=year-of-the-owl
| Not valid before: 2024-12-18T09:02:00
|_Not valid after:  2025-06-19T09:02:00
|_ssl-date: 2024-12-19T09:07:19+00:00; -1s from scanner time.

┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/windows/yearoftheowl]
└─$ nmap -p 47001 10.10.193.121            
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-12-19 18:34 IST
Nmap scan report for 10.10.193.121
Host is up (0.42s latency).

PORT      STATE SERVICE
47001/tcp open  winrm

Nmap done: 1 IP address (1 host up) scanned in 1.32 seconds




