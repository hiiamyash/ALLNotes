
WHat is libc 

what is dynamically linked and statically linked

What is Stripped and Non-stripped Binary

# Static ANa;ysis
```
strings
```

```
nm
```

```
ldd
```

```
readelf -a binary_name
```
`Does the entire staic analysis of the binary`
# Dynamic Analyisis

### ltrace

![](../../attchments/Pasted%20image%2020260327173320.png)

```
ltrace ./crackme2
```
The ABove helps in dynamicaly Analics of the BInary and print all the imp ffuctions calls  of the binary

![](../../attchments/Pasted%20image%2020260327173701.png)

```
ltrace ./crackme1 asdfgh
```
`Above will pass an argument`

### strace


