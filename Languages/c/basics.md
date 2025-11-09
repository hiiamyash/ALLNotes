The statements are executed, one by one, in the same order as they are written:


When you are working with text, it must be wrapped inside double quotations marks `""`.



You can use as many `printf()` functions as you want. **However**, note that it does not insert a new line at the end of the output:


To insert a new line, you can use the `\n` character:

```
#include <stdio.h>  
  
int main() {  
  printf("Hello World!**\n**");  
  printf("I am learning C.");  
  return 0;  
}

one more method of insesting new line 

printf("Hello World!**\n**I am learning C.**\n**And it is awesome!");

```

Two `\n` characters after each other will create a blank line:


|Escape Sequence|Description|Try it|
|---|---|---|
|\t|Creates a horizontal tab||

|     |                                   |     |
| --- | --------------------------------- | --- |
| \\\ | Inserts a backslash character (\) |     |
| \\" | Inserts a double quote character  |     |

# C Comments


Single-line comments start with two forward slashes (`//`).

```
// This is a comment  
printf("Hello World!");
```

Multi-line comments start with `/*` and ends with `*/`.

Any text between `/*` and `*/` will be ignored by the compiler:

```
/* The code below will print the words Hello World!  
to the screen, and it is amazing */  
printf("Hello World!");
```



# Preprocessor


Before a c progam is compiled i a compiler ,source code is proessed by a proogram .
The pre processor diretive starts with # symbol nd do dnot require a semicolonn at the end .
Pre processor directiveare executd before compilation.



Advantages of preprocessor -

code Reusability 
macro expansion 
conditional compilational
Function -like Macros
