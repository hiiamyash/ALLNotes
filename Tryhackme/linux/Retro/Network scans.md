

## rustscans

Open 10.10.16.78:80
Open 10.10.16.78:3389

## nmap


┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/linux/retro]
└─$ nmap -p 80,3389 -A -T4 retro.thm -Pn
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-06 23:07 IST
Nmap scan report for retro.thm (10.10.16.78)
Host is up (0.53s latency).

PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS httpd 10.0
|_http-title: IIS Windows Server
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| ssl-cert: Subject: commonName=RetroWeb
| Not valid before: 2025-01-05T17:24:56
|_Not valid after:  2025-07-07T17:24:56
|_ssl-date: 2025-01-06T17:38:19+00:00; -1s from scanner time.






┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/linux/retro]
└─$ nmap --script "rdp-enum-encryption or rdp-vuln-ms12-020 or rdp-ntlm-info" -p 3389 -T4 retro.thm -Pn
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-06 23:12 IST
Nmap scan report for retro.thm (10.10.16.78)
Host is up (0.40s latency).

PORT     STATE SERVICE
3389/tcp open  ms-wbt-server
| rdp-enum-encryption: 
|   Security layer
|     CredSSP (NLA): SUCCESS
|     CredSSP with Early User Auth: SUCCESS
|_    RDSTLS: SUCCESS
| rdp-ntlm-info: 
|   Target_Name: RETROWEB
|   NetBIOS_Domain_Name: RETROWEB
|   NetBIOS_Computer_Name: RETROWEB
|   DNS_Domain_Name: RetroWeb
|   DNS_Computer_Name: RetroWeb
|   Product_Version: 10.0.14393
|_  System_Time: 2025-01-06T17:42:32+00:00




