
```
checksec binary_name
```
`To check the seurity implemented by that binary`
![](../../attchments/Pasted%20image%2020260329171740.png)
We can see Packer Being found


WHat are packers?
Like suppose you have a normal binary and you are using a packer to compress its size. And also it now becomes unreadable even if you use tools like strings and other tools you can't read the content inside it. it also adds some code that tells you how to unpack that binary(back to it's original code) so it can be runned and the Linux can understand it.

THe Crackme7 Binary is packed with UPX which is an famous packer

```
upx -d binary_name -o binary_update_name
```

```
b main
```
`gdb command help to add breakpoint to the main`

![](../../attchments/Pasted%20image%2020260330223555.png)
**THe above image shows that an Password() function is being called that is inside the Password Class**
***THe above is also an Contrustor Because The class name and the Function name is the same***


![](../../attchments/Pasted%20image%2020260330224035.png)
***After we step into the contructor we see that it is also calling the get_password() fuction from the passowrd class***

```
pwndbg> p 0xb
$1 = 11
```
`convert hex too dec using gdb`

