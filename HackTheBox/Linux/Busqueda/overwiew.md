First I am going to do an rust scan and an nmap scan  
rustscan -a 10.10.11.208  
.----. .-. .-. .----..---. .----. .---. .--. .-. .-.  
| {} }| { } |{ {__ {_ _}{ {__ / ___} / {} \ | `| |  
| .-. \| {_} |.-._} } | | .-._} }\ }/ /\ \| |\ |  
`-' `-'`-----'`----' `-' `----' `---' `-' `-'`-' `-'  
The Modern Day Port Scanner.  
________________________________________  
: [http://discord.skerritt.blog](http://discord.skerritt.blog) :  
: [https://github.com/RustScan/RustScan](https://github.com/RustScan/RustScan) :  
--------------------------------------  
Port scanning: Because every port has a story to tell.
 
[~] The config file is expected to be at "/home/kali/.rustscan.toml"  
[!] File limit is lower than default batch size. Consider upping with --ulimit. May cause harm to sensitive servers  
[!] Your file limit is very small, which negatively impacts RustScan's speed. Use the Docker image, or up the Ulimit with '--ulimit 5000'.  
Open 10.10.11.208:22  
Open 10.10.11.208:80
    
-----------nmap
   

nmap searcher.htb -p 22,80 -sV -sC -A  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2024-10-17 16:01 IST  
Nmap scan report for searcher.htb (10.10.11.208)  
Host is up (0.58s latency).
 
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 8.9p1 Ubuntu 3ubuntu0.1 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 256 4f:e3:a6:67:a2:27:f9:11:8d:c3:0e:d7:73:a0:2c:28 (ECDSA)  
|_ 256 81:6e:78:76:6b:8a:ea:7d:1b:ab:d4:36:b7:f8:ec:c4 (ED25519)  
80/tcp open http Apache httpd 2.4.52  
| http-server-header:  
| Apache/2.4.52 (Ubuntu)  
|_ Werkzeug/2.1.2 Python/3.10.6