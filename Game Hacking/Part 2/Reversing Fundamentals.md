
The best way to start reversing a game is to figure out what you
want to look at and then find where it is

if an particluar text appers before that action then try to find that text anything you do you will have to use breakpoints


`Breakpoints` allow the debugger to pause execution of the game at a specific
instruction.

## Memory Breakpoint

In part 1 we found the mmemeory location of the gold we can add an breakpoint to the location to uderstand the logic

## Code Breakpoint

if we do not have the memory address then


A code breakpoint is a way to find a hidden piece of code by using a unique clue. Since we can't find the `draw_wall` function directly, we instead look for something it does, like printing the error message "Couldn't find wall texture." Using a special tool called a debugger, we tell the game to pause the very moment it tries to print that specific message. When we force the error to happen, the game freezes exactly where we told it to. From that paused spot, we can then work backward (a process called "stepping out") to find the original `draw_wall` function that sent us there, allowing us to disable it.

## nop instruction

A nop (opcode 0x90) stands for no operation. When encountering this instruction, a
CPU will do nothing and continue on to the next instruction. This behavior can be used
to modify game logic.

![[Pasted image 20250817134344.png]]

By replacing the sub operation with a nop, the game will no longer subtract our gold.


