
The goal here is going to be first find the memory location of the golad then we will change the assembly code SO that when we will recruit the players form the game it will not affect the Acctual gold so we can recuit unlimited paylers with buying the extra goald

## Step 1 

`Getting the Gold variable memryy addres`

We are running the game and the cheat engine 

![Pasted image 20250818162006](../../attchments/Pasted%20image%2020250818162006.png)

THe cuurent value of golad was 150 so we Entered the 150 value and Clciked the first scan

![Pasted image 20250818162207](../../attchments/Pasted%20image%2020250818162207.png)

Now we will recruit some new player and this will affect the golad number then will will do the next scan

![Pasted image 20250818162443](../../attchments/Pasted%20image%2020250818162443.png)

We got the memory addess

`088CB12C`


## Step 2

Now we will go to the debugger

Now we will attach the process
![Pasted image 20250818162718](../../attchments/Pasted%20image%2020250818162718.png)

We will right click on the dump section and then `go to` and then `expression`

then enter the memory address

THen we will right click on the value of the varialble
![Pasted image 20250818163738](../../attchments/Pasted%20image%2020250818163738.png)
`Breakpoint` `Hardware write` `Dword`

Now go to the game and try to recruit an player as soon as we try that the game will pause and this will happen in the debugger

![Pasted image 20250818164214](../../attchments/Pasted%20image%2020250818164214.png)

above we can see the lines resposible for changeing our gold the `sub` instruction is probly being used to subtracting our gold value so we can chnage that instruction to an `nop` instruction

Now we will reight click on the sub instructio then
`Binary` `Fill with Nops`

![Pasted image 20250818164602](../../attchments/Pasted%20image%2020250818164602.png)


Now remove the breakpoints 
![Pasted image 20250818164927](../../attchments/Pasted%20image%2020250818164927.png)
And try to recuit more troops and iit will not have any affect on the goald value


