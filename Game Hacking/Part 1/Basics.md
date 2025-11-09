

What is CPU 
WHaat are registers

Types of instructions in assemby
Add two numbers.
Subtract two numbers.
Compare two numbers.
Move a number into a section of memory (RAM).
Go to another section of code


# Game Fucdamentals

## Game Parts 

While games are applications, they are complex and made up of several parts. Some of
these include:

Graphics
Sounds
Input
Physics
Game logic


If you want to make an wall hack than you will have to modify the DirectX it will come under Graphic section and if you want to make an money hack then you will have to Change the game logic and it's code.

## Game Structure 

Most games have two major functions:

- Setup
- Main Loop

The Setup will have fuctions that will run at the execution of the file like Loding images creating memeory in the process etc.

THe main loop will have fuction that will keep runing till the program is not closed like Updateing the screen or the score board etc.

![Pasted image 20250816202700](Pasted%20image%2020250816202700.png)
![Pasted image 20250816202707](Pasted%20image%2020250816202707.png)

Understand `for` loops in C and variables  



Classes are
usually self-contained. For example, many games will have a Player class. This class will
contain several variables like the player's position, name, or money. These variables
inside the class are known as members. Classes will also contain functions to modify
these members. One example of a Player class might look like:


```c
class Player {
	int money;
	string name;
	function increase_money() {
		money = money + 1;
}

```


## MEmory

A lot of data of game is in the hard ware but when it is executed it loads in the ram Because games are so large, they must
constantly load different data from the RAM into registers to operate on. This loading is
typically done by a mov command.


## Multiiiple Clients

![Pasted image 20250816210433](Pasted%20image%2020250816210433.png)

Each client are the players in an multiplayer game and each client will have an copy of thier game and the server is how they will communtae will other clients and the game itself

If a cleint moves x direction then it will tell thee server to update it's position

## Multiple servers

While the client represents each player's copy of the game, the server ensures that all
the connected clients are playing the same copy of the game. Servers will often restrict
what changes they accept from clients. For example, imagine we wrote a hack to
change our money in a game. If it is a multiplayer game, the server will reject our
changes. This is why single-player hacks will often not work in multiplayer


