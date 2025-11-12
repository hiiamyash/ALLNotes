![[Exported image 20241213183456-0.png|Exported image]]  
![[Exported image 20241213183458-1.png|Exported image]]  
![[Exported image 20241213183501-2.png|Exported image]]  
![[Exported image 20241213183503-3.png|Exported image]]  
![[Exported image 20241213183509-4.png|Exported image]]  
![[Exported image 20241213183511-5.png|Exported image]]  
![[Exported image 20241213183513-6.png|Exported image]]  
![[Exported image 20241213183518-7.png|Exported image]]

V or visual mode and p for secound visual mode
 
Prees q to go to the normal format

![[Exported image 20241213183520-8.png|Exported image]]

Vv to enter visual graph mode

![[Exported image 20241213183523-9.png|Exported image]]

Capital r to change the colous scheme  
P to change the visual mode

![[Exported image 20241213183525-10.png|Exported image]]

Capital s to move down

![[Exported image 20241213183531-11.png|Exported image]]

The value of edi is aruc arumentcounter

![[Exported image 20241213183533-12.png|Exported image]]

If the number of argument is greater than jump jg jump if greater

![[Exported image 20241213183535-13.png|Exported image]]  
![[Exported image 20241213183538-14.png|Exported image]]

If argument is less than 1 than it will print argument is missing

![[Exported image 20241213183541-15.png|Exported image]]

Memory addres of each variable

![[Exported image 20241213183543-16.png|Exported image]]

Press : to get command promt

![[Exported image 20241213183547-17.png|Exported image]]

We are seeing whats inside variable var_34h

![[Exported image 20241213183553-18.png|Exported image]]  
![[Exported image 20241213183558-19.png|Exported image]]

The valuse of variable is 1 soit wil not jump

![[Exported image 20241213183601-20.png|Exported image]]  
![[Exported image 20241213183603-21.png|Exported image]]

Dc means continue the program from there tehn press enter to go back to the visual mode

![[Exported image 20241213183606-22.png|Exported image]]

Ood will restart the program with a new argument dc we hit the breakpoint

![[Exported image 20241213183608-23.png|Exported image]]

Capital s will throw you to the starting of the program or the break point

![[Exported image 20241213183611-24.png|Exported image]]

Assemble takes the file name as an argument and you also provided an argument 12345678 so the var34h has 2

![[Exported image 20241213183616-25.png|Exported image]]

Now it will jump to true

![[Exported image 20241213183619-26.png|Exported image]]  
![[Exported image 20241213183623-27.png|Exported image]]

If the length of the code is same the it will jump to true if not then wring password

![[Exported image 20241213183628-28.png|Exported image]]  
![[Exported image 20241213183631-29.png|Exported image]]

We gave an string of length 8 and it is comaring it tio the length hex16 which is the length of the original password so it is false

![[Exported image 20241213183633-30.png|Exported image]]

So rbx has 22 lenght input

![[Exported image 20241213183636-31.png|Exported image]]  
![[Exported image 20241213183641-32.png|Exported image]]  
![[Exported image 20241213183643-33.png|Exported image]]  
![[Exported image 20241213183646-34.png|Exported image]]

Adding the breakpoint too the cmp string length

![[Exported image 20241213183650-35.png|Exported image]]  
![[Exported image 20241213183653-36.png|Exported image]]  
![[Exported image 20241213183656-37.png|Exported image]]

Now the value is equal so it will take the jump

![[Exported image 20241213183659-38.png|Exported image]]

Strcmp directly compares the strings it comparing iif the original passowrd and user password is same or not

![[Exported image 20241213183706-39.png|Exported image]]

In strcmp fist value goes in rdi and secound in rsi

![[Exported image 20241213183708-40.png|Exported image]]  
![[Exported image 20241213183711-41.png|Exported image]]  
![[Exported image 20241213183713-42.png|Exported image]]