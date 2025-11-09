Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-16 14:28 IST
Nmap scan report for 10.10.204.101
Host is up (0.47s latency).

PORT      STATE SERVICE      VERSION
80/tcp    open  http         Microsoft IIS httpd 7.5
|_http-server-header: Microsoft-IIS/7.5
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-title: 404 - File or directory not found.
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Home Basic 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
3306/tcp  open  mysql        MariaDB (unauthorized)
8080/tcp  open  http         Apache httpd 2.4.23 (OpenSSL/1.0.2h PHP/5.6.28)
|_http-server-header: Apache/2.4.23 (Win32) OpenSSL/1.0.2h PHP/5.6.28
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-title: Index of /
| http-ls: Volume /
| SIZE  TIME              FILENAME
| -     2019-04-11 22:52  oscommerce-2.3.4/
| -     2019-04-11 22:52  oscommerce-2.3.4/catalog/
| -     2019-04-11 22:52  oscommerce-2.3.4/docs/
|_
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49158/tcp open  msrpc        Microsoft Windows RPC
49159/tcp open  msrpc        Microsoft Windows RPC
49160/tcp open  msrpc        Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Microsoft Server 2008 R2 SP1 (96%), Microsoft Windows 7 or 8.1 R1 or Server 2008 R2 SP1 (93%), Microsoft Windows 7 or 8.1 R1 (93%), Microsoft Windows 8.1 (93%), Microsoft Windows 7 or Windows Server 2008 R2 (92%), Microsoft Windows 10 (91%), Microsoft Windows 10 10586 - 14393 (91%), Microsoft Windows 10 1511 (91%), Microsoft Windows 10 1607 (91%), Microsoft Windows Home Server 2011 (Windows Server 2008 R2) (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 4 hops
Service Info: Hosts: BLUEPRINT, localhost; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_nbstat: NetBIOS name: BLUEPRINT, NetBIOS user: <unknown>, NetBIOS MAC: 02:26:ff:10:27:8f (unknown)
| smb2-time: 
|   date: 2025-01-16T08:57:15
|_  start_date: 2025-01-16T08:54:53
| smb-os-discovery: 
|   OS: Windows 7 Home Basic 7601 Service Pack 1 (Windows 7 Home Basic 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: BLUEPRINT
|   NetBIOS computer name: BLUEPRINT\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2025-01-16T08:57:15+00:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2:1:0: 
|_    Message signing enabled but not required
|_clock-skew: mean: -2m41s, deviation: 1s, median: -2m42s

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   499.86 ms 10.13.0.1
2   ... 3
4   500.01 ms 10.10.204.101

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 98.36 seconds


Open 10.10.204.101:80
Open 10.10.204.101:135
Open 10.10.204.101:139
Open 10.10.204.101:443
Open 10.10.204.101:3306
Open 10.10.204.101:8080
Open 10.10.204.101:49152
Open 10.10.204.101:49160
Open 10.10.204.101:49159
Open 10.10.204.101:49154
Open 10.10.204.101:49153
Open 10.10.204.101:49158
