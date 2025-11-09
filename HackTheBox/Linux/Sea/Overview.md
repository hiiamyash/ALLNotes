![Exported image](Exported%20image%2020241213184410-0.png)

PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 3072 4b:89:47:39:67:3d:07:31:5e:3f:4c:27:41:1f:f9:67 (RSA)  
| 256 04:a7:4f:39:95:65:c5:b0:8d:d5:49:2e:d8:44:00:36 (ECDSA)  
|_ 256 b4:5e:83:93:c5:42:49:de:71:25:92:71:23:b1:85:54 (ED25519)  
443/tcp open ssl/http nginx 1.18.0 (Ubuntu)  
|_http-server-header: nginx/1.18.0 (Ubuntu)  
|_http-title: 400 The plain HTTP request was sent to HTTPS port  
|_ssl-date: TLS randomness does not represent time  
| tls-nextprotoneg:  
|_ http/1.1  
| ssl-cert: Subject: commonName=seal.htb/organizationName=Seal Pvt Ltd/stateOrProvinceName=London/countryName=UK  
| Not valid before: 2021-05-05T10:24:03  
|_Not valid after: 2022-05-05T10:24:03  
| tls-alpn:  
|_ http/1.1  
8080/tcp open http-proxy  
| http-auth:  
| HTTP/1.1 401 Unauthorized\x0D  
|_ Server returned status 401 but no WWW-Authenticate header.  
|_http-title: Site doesn't have a title (text/html;charset=utf-8).  
| fingerprint-strings:  
| FourOhFourRequest:  
| HTTP/1.1 401 Unauthorized  
| Date: Mon, 11 Nov 2024 15:04:05 GMT  
| Set-Cookie: JSESSIONID=node017b40jzm2px801bubxbxpudo782.node0; Path=/; HttpOnly  
| Expires: Thu, 01 Jan 1970 00:00:00 GMT  
| Content-Type: text/html;charset=utf-8  
| Content-Length: 0  
| GetRequest:  
| HTTP/1.1 401 Unauthorized  
| Date: Mon, 11 Nov 2024 15:04:02 GMT  
| Set-Cookie: JSESSIONID=node0m5n7cv6dblgl11q0dzeaol8440.node0; Path=/; HttpOnly  
| Expires: Thu, 01 Jan 1970 00:00:00 GMT  
| Content-Type: text/html;charset=utf-8  
| Content-Length: 0  
| HTTPOptions:  
| HTTP/1.1 200 OK  
| Date: Mon, 11 Nov 2024 15:04:03 GMT  
| Set-Cookie: JSESSIONID=node01lr7sgpsswu7e10ay2kcxk41t11.