```
. { iwr -useb https://boxstarter.org/bootstrapper.ps1 } | iex;
Get-Boxstarter -Force


Install-BoxstarterPackage -PackageName https://
raw.githubusercontent.com/GameHackingAcademy/vmsetup/master/
vmsetup.txt -DisableReboots
```


```
Install-BoxstarterPackage -PackageName C:
\location\of\vmsetup.txt -DisableReboots
```

