
jne - jump if not singned flag

```
info registeros
```
![](../../attchments/Pasted%20image%2020260329160522.png)
SF - Singned Flag

if see the falg of the falg there that means it's value is one

in crackme6
![](../../attchments/Pasted%20image%2020260329160722.png)
in the above ther is jns but it's value is 1 so it will not jump


![](../../attchments/Pasted%20image%2020260329160851.png)
in the above image it  shows that the bianry  is using an Anti Deguub Protection

![](../../attchments/Pasted%20image%2020260329161059.png)
`ptrace` call is being used to identify if any debugbber is being used or not

![](../../attchments/Pasted%20image%2020260329161212.png)

```
c
```
`Contiue to the next breakpoint`


![](../../attchments/Pasted%20image%2020260329161410.png)
in the above image the test instrction works like this if raw = 0 then it passes and it will take an jump bypassiing the check

```
set $rax = 0
```
`Changes the value of rax to 0`

use  binary ninja to patch the binary if always brach means green and nver branvh means the red

take the dcompiler code and covert it into python
