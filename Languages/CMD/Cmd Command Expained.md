
```cmd-session
runas /netonly /user:INLANEFREIGHT\adunn powershell
```

**`/netonly`****The most critical flag.** It tells Windows: _"Use my current local credentials for everything on this computer, but use the credentials I provide here for any **network** connections."_


