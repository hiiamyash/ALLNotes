
- Web application config files  
    
- Service configuration files
- Registry keys
- Centrally deployed applications


Configuration File Credentials  

However, we will focus on recovering credentials from a centrally deployed application in this task. Usually, these applications need a method to authenticate to the domain during both the installation and execution phases. An example of such as application is McAfee Enterprise Endpoint Security, which organisations can use as the endpoint detection and response tool for security.  

McAfee embeds the credentials used during installation to connect back to the orchestrator in a file called ma.db. This database file can be retrieved and read with local access to the host to recover the associated AD service account. We will be using the SSH access on THMJMP1 again for this exercise.

The ma.db file is stored in a fixed location:


so fins the ma.db file then open in 

```
thm@thm:# sqlitebrowser ma.db
```

copy thr ensrypted hash and decrypt it using this python script

https://github.com/funoverip/mcafee-sitelist-pwd-decryption


	