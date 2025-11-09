80/tcp open http Apache httpd 2.4.41 ((Ubuntu))

![Exported image](Exported%20image%2020241213185359-0.png)

TO-DO  
-gobuster   /.php (Status: 403) [Size: 276]  
/index.php (Status: 302) [Size: 0] [--> login.php]  
/.html (Status: 403) [Size: 276]  
/login.php (Status: 200) [Size: 848]  
/css (Status: 301) [Size: 308] [--> [http://opacity.thm/css/](http://opacity.thm/css/)]  
/logout.php  
/cloud (Status: 301) [Size: 310] [--> [http://opacity.thm/cloud/](http://opacity.thm/cloud/)]
 
-dirsearch  
-nikto
    
nikto -h [http://opacity.thm](http://opacity.thm)  
- Nikto v2.5.0  
---------------------------------------------------------------------------  
+ Target IP: 10.10.70.251  
+ Target Hostname: opacity.thm  
+ Target Port: 80  
+ Start Time: 2024-09-05 00:10:31 (GMT5.5)  
---------------------------------------------------------------------------  
+ Server: Apache/2.4.41 (Ubuntu)  
+ /: The anti-clickjacking X-Frame-Options header is not present. See: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)  
+ /: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type. See: [https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/](https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/)  
+ /: Cookie PHPSESSID created without the httponly flag. See: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)  
+ Root page / redirects to: login.php  
+ No CGI Directories found (use '-C all' to force check all possible dirs)  
+ Apache/2.4.41 appears to be outdated (current is at least Apache/2.4.54). Apache 2.2.34 is the EOL for the 2.x branch.  
+ /login.php: Admin login page/section found.  
+ 7962 requests: 0 error(s) and 5 item(s) reported on remote host  
+ End Time: 2024-09-05 01:07:49 (GMT5.5) (3438 seconds)
      

-sqlinjection  
-vhost  
-nosql  
-clusterbomb  
-username enum  
-source code
 
----/cloud directory looks intresting

![Exported image](Exported%20image%2020241213185404-1.png)

Bypassing file extension filters
 ![Exported image](Exported%20image%2020241213185406-2.png)  
![Exported image](Exported%20image%2020241213185409-3.png)

[http://10.10.102.197/cloud/images/shell.php](http://10.10.102.197/cloud/images/shell.php)

![Exported image](Exported%20image%2020241213185411-4.png)