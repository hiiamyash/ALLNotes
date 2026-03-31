![](../../attchments/Pasted%20image%2020260326162039.png)

### Input Handling
- **`puts`**: Prints the value pointed to by the `rdi` register.
- **`gets`**: Takes input from the user.
  - *Note:* `rdi` holds the memory address where the `gets` function will store the user input.

### Key Instructions
- **`lea` (Load Effective Address)**:
  - Works similarly to the `mov` instruction, but instead of moving the *value* at an address, it moves the **address** itself.
  - *Example:* `lea rax, [rbp+s]` moves the address of `rbp+s` into `rax`. (If it were `mov`, it would store the value at that address in `rax`).

### Control Flow

Strlen function does this : whatever value is in the RDI its length will get returned in RAX 
- **Input Length Check**:
  - If the input length is `0Bh` (11 in decimal), the program jumps to the next part.
  - *Note:* Agar input length `0Bh` nahi hai, toh "Wrong Password" error aayega.
- **Jump Instructions**:
  - `jl`: Jump if Less.
  - `jnz` / `jne`: **Jump if Not Zero** is the same as **Jump if Not Equal**.

### Register Details
- `rax`: The last byte is `al`.
- `rdx`: The last byte is `dl`.



![](../../attchments/Pasted%20image%2020260326163456.png)

eax holds the lenght of the user input which is move to var_40 and var_44 hods 0 as value 

then var_44 value is move to eax(which is 0) and then cmp compares 0 value with the lenght of the user input var_40
 jl jump if less then 0 now user iput can never be less then 0 in lenght 


Add Break Point to The Cmp statements and USe F9 to Contiue Process and USe F8 to step into 

JBZ - **less than or equal to 29**

