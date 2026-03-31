What is Patching

what is the difference between cracked softeware and patched software

Crackme 4

Using Binary Ninja for Disassembly and Decompiling and also FOr patching

![](../../attchments/Pasted%20image%2020260328015412.png)
``
```
objdump -D crackme4 -M intel --disassembly=main
```
`The above will print the disassembley of main fuction`

![](../../attchments/Pasted%20image%2020260328015619.png)

In the above image 75 0E are the op codes this helps the computer to underatnd the assembly
**75 represents the jne** and **0E present the offset it means the difference bettwent the current address to the address it wants to jump on**

**Now what if you change the op code of jne to the op code of je then it will change it **


```
ghex binary_name
```
`Graphical hex editor`

![](../../attchments/Pasted%20image%2020260328020327.png)

