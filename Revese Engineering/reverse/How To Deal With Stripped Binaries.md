
pwndbg

first we need to find the main fuction

when an binary get executed then
start function (.text section)---->libc_start_main fcution----->main 

The address of the .text section is the starting of the start fuction in assembley
Before calling the libc_start_main fuction this fuction take the address of the main fuciton as it's first argument in the RDI register

```
start
```
`Use this in gdb to get to the start func`

```
disassemble fuction_name
```

```
x/30i $rip
```
`this is called examine(x) this print the 30 instruciton(i) of the fuction that is in the rip(rip contains the memory address of the function getting executed)`

```
ni
```
`Next INstrction`

![](../../attchments/Pasted%20image%2020260328214500.png)
the libc_start_main is takeing the memory address of the main which is in the RDI SO now you have the address of the main fuction

```
si
```
`Step into an function`

```
nearpc 27
```
`Will print 27 instrction after the rip address`

![](../../attchments/Pasted%20image%2020260328230752.png)

```
x/s hex_value
```
`Will print the hex value in string format`

```
unhex hex_value
```
`Works for pwndbg`

