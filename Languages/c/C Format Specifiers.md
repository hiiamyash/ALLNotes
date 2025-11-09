Format specifiers are used together with the `printf()` function to tell the compiler what type of data the variable is storing. It is basically a **placeholder** for the variable value.

A format specifier starts with a percentage sign `%`, followed by a character.

For example, to output the value of an `int` variable, use the format specifier `%d` surrounded by double quotes (`""`), inside the `printf()` function:

```
int myNum = 15;  
printf("%d", myNum);  // Outputs 15
```

To print other types, use `%c` for `char` and `%f` for `float`:

```c
// Create variables  
int myNum = 15;            // Integer (whole number)  
float myFloatNum = 5.99;   // Floating point number  
char myLetter = 'D';       // Character  
  
// Print variables  
printf("%d\n", myNum);  
printf("%f\n", myFloatNum);  
printf("%c\n", myLetter);
```

```
int myNum = 15;  
char myLetter = 'D';  
printf("My number is %d and my letter is %c", myNum, myLetter);
```



You can also just print a value without storing it in a variable, as long as you use the correct format specifier:

```
printf("My favorite number is: %d", 15);  
printf("My favorite letter is: %c", 'D');
```


# C Variable Values

If you assign a new value to an existing variable, it will **overwrite** the previous value:

```
int myNum = 15;  // myNum is 15  
myNum = 10;  // Now myNum is 10
```

ou can also assign the value of one variable to another:

```
int myNum = 15;  
  
int myOtherNum = 23;  
  
// Assign the value of myOtherNum (23) to myNum  
myNum = myOtherNum;  
  
// myNum is now 23, instead of 15  
printf("%d", myNum);
```

To add a variable to another variable, you can use the `+` operator:

```
int x = 5;  
int y = 6;  
int sum = x + y;  
printf("%d", sum);
```

```
#include<stdio.h>
#include<stdlib.h>
int main(){
    int rows,cols;
    int**array;
    printf("Enter the number of rows:");
    scanf("%d,&rows");
    printf("Enter the number of columns:");
    scanf("%d",&cols);
    array=(int **)malloc(rows*sizeof(int));
    for (int i = 0; i < rows; i++)
    {
        array[i]=(int*)malloc(cols*sizeof(int));
    }
     array=(int **)malloc(cols*sizeof(int));
    for (int j = 0; j < cols; j++)
    {
        array[j]=(int*)malloc(cols*sizeof(int));
    }

    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; i <cols; j++)
        {
        printf("Element [%d][%d]:",i,j);
        scanf("%d",&array[i][j]);
        }
    printf("\nOrignal Array:\n");
    for(int i=0;i<rows;i++){
        for(int j=0;j<cols;j++){
            printf("%d",array[i][j]);
        }
    }
    printf("\n");
    }
    return 0;
    
    
}
```


# C Declare Multiple Variables

o declare more than one variable of the same type, use a **comma-separated** list:

```
int x = 5, y = 6, z = 50;  
printf("%d", x + y + z);
```


# C Data Types

|Data Type|Size|Description|Example|
|---|---|---|---|
|`int`|2 or 4 bytes|Stores whole numbers, without decimals|`1`|
|`float`|4 bytes|Stores fractional numbers, containing one or more decimals. Sufficient for storing 6-7 decimal digits|`1.99`|
|`double`|8 bytes|Stores fractional numbers, containing one or more decimals. Sufficient for storing 15 decimal digits|`1.99`|
|`char`|1 byte|Stores a single character/letter/number, or ASCII values|`'A'`|

|Format Specifier|Data Type|Try it|
|---|---|---|
|`%d` or `%i`|`int`||

|   |   |   |
|---|---|---|
|`%f` or `%F`|`float`||
|`%lf`|`double`||
|`%c`|`char`||
|`%s`|Used for **[strings](https://www.w3schools.com/c/c_strings.php) (text)**, which you will learn more about in a later chapter|

To store multiple characters (or whole words), use [strings](https://www.w3schools.com/c/c_strings.php) (which you will learn more about in a later chapter):




Array of pointers

```
#inclue <stdio.h>
int main()
{
int var1=10; intn var2 = 20; int var3 = 30;
int *ptr

}


```