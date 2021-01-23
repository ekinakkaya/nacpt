# nacpt (ANSI C)

**Not a C Programming Tutorial :)**

*Written by Ekin Akkaya.*

This cheatsheet includes short explanations and usages of various functions and features of C, useful and small programs/libraries that are yoinked from an external source or implemented by me.

**Note: Most of this cheatsheet is validated and written by taking [this](https://www.amazon.com.tr/Programming-Language-Brian-W-Kernighan/dp/0131103628) book as referance.**

<!--
TODO:add tags&f-names and such. Think about searching methods or keys like tag or f. add slib as a key?
-->
<!--
You can search with Ctrl+F such as "f:somefunction" or "tag:sometag". All tags and function names will be included at the end of the document.
-->


<br><hr>

# What's inside?
<!--
- [gcc General Usage](#gcc-general-usage)
- [Arrays](#arrays)
-->
- [gcc General Usage](#gcc-general-usage)
- [stdio.h](#stdioh)
- [printf()](#printf)
- [Variables](#variables)
- [For Statement](#for-statement)
- [Symbolic Constants](#symbolic-constants)
- [getchar() and putchar()](#getchar-and-putchar)
- [Arrays](#arrays)
- [Functions](#functions)
- [Types & Operators & Expressions](#types--operators--expressions)
- [Declarations](#declarations)
- [Bitwise Operators](#bitwise-operators)
- [Bitwise Facts](#bitwise-facts)
- [Bits Manipulation](#bits-manipulation)
- [Bitwise Hacks & Tricks](#bitwise-hacks--tricks)


<br><hr>

# stdio.h
```C
#include <stdio.h>
```
Standard library header. stdio stands for **standard input/output**.

For more info, see *[this](https://pubs.opengroup.org/onlinepubs/7908799/xsh/stdio.h.html)*.
Or *[this](https://www.tutorialspoint.com/c_standard_library/stdio_h.htm)*.

<br>

# printf()
printf is a library function that prints the output.

```C
#include <stdio.h>
int main() {
    printf("hello world.\n");
}
```

Note: **'\n'** stands for *newline character*.

Example with an *int* and *format specifiers*:
```C
#include <stdio.h>

int main() {
    int var_int = 30;
    float var_float = 3.1415;

    /* Print. */
    printf("int: %d", var_int);
    /* Print at least 6 characters wide. */
    printf("int: %6d", var_int);

    /* Print at least 6 characters wide,
     * and 2 after decimal point. */
    printf("float: %6.2f", var_float);
    
    return 0;
}
```
For more info on *format specifiers*, see [Variables](#variables). 

<br>

# Variables

Let's define an integer. An integer can hold up to 2 or 4 bytes, which means it can be any number between *−32,767, +32,767* *-2,147,483,648 to 2,147,483,647*. This **changes** depending on the compiler and the processor that you're using.
For more info, see *[this](https://en.wikipedia.org/wiki/C_data_types)*. Or *[this](https://www.tutorialspoint.com/cprogramming/c_data_types.htm)*

```C
#include <stdio.h>

int main() {
    /* Defining an integer */
    int variable_name = 10;

    /* Printing the integer */
    printf("variable_name value: %d\n", variable_name);
    return 0;
}
```

Btw, the '%d' in the printf function is a **format specifier** that prints the integer. (For more info, see *[this](https://www.tutorialspoint.com/format-specifiers-in-c)*.) The '%' sign is a specifier and the 'd' stands for *'decimal'*. '%i' can be used for the same purpose.

Let's look at the other integer types.

```C
#include <stdio.h>

int main() {
    int var_int;
    printf("int: %i\n", var_int);
    printf("same int: %d\n", var_int);

    float var_float;
    printf("float: %f\n", var_float);



    return 0;
}
```

<br>

# For Statement

Example Usage:
```C
#include <stdio.h>

int main() {
    int i;
    for (i = 0; i < 10; i++) {
        printf("Loop %d\n", i);
    }

    return 0;
}
```

<br>

# While Statement

Example Usage:
```C
#include <stdio.h>

int main() {
    int i;
    while (i < 10) {
        printf("Loop %d\n", i);
        i++;
    }

    return 0;
}
```

<br>

# Symbolic Constants

Example Usage:
```C
#include <stdio.h>

#define NUMBER         200
#define ANOTHER_NUMBER 30
#define PI             3.1415

int main() {
    printf("%d\n", NUMBER);
    printf("%d\n", ANOTHER_NUMBER);
    printf("%f\n", PI);

    return 0;
}
```

<br>

# getchar() and putchar()

Each time it's called, *getchar* reads the next input character from a text stream and returns it.

Example Usage:
```C
#include <stdio.h>
#include <string.h>

int main() {
    int c;
    c = getchar();

    putchar(c);

    return 0;
}
```

Program that copies it's input to it's output:
```C
#include <stdio.h>

int main() {
    int c;
    c = getchar();         /* read a character         */
    while (c != EOF) {
        putchar(c);        /* output the character     */
        c = getchar();     /* read a character (again) */
    }

    return 0;
}
```

Another version:
```C
#include <stdio.h>

int main() {
    int c;
    while (getchar() != EOF) {
        putchar(c); /* output the character */
    }
    return 0;
}
```

<br>

# Arrays

Integer Array:
```C
#include <stdio.h>

int main() {
    int int_array[10];
    int_array = {3, 4, 2, 12, 23, 56, 25, 74, 42, 80};

    for (int i = 0; i < 10; i++)
        printf("int_array[%d] = %d\n", i, int_array[i]);
    
    return 0;
}
```
Note: Indices of an array always start at zero (0).


Character Array:
```C
#include <stdio.h>

int main() {

    return 0;
}
```

<br>

# Functions

Example function:
```C
#include <stdio.h>

int power(int m, int n); /* Function declaration */

int power(int base, int n) {
    int i, p;
    p = 1;
    for (i = 1; i <= n; ++i) {
        p = p * base;
    }
    return p;
}

int main() {
    printf("power of 2 to 5: %d\n", power(2,5));

    return 0;
}
```

Note: Function definitions can be in any order. 

<br>

# Types & Operators & Expressions

Data Types | Description
--- | ---
char | a single byte, capable of holding one character in the local caracter set
int | an integer
float | single-precision floating point
double | double-precision floating point

**short** and **long** qualifiers can be applied.
```c
short int i;
long int counter;
```


Enumeration:
```c
/* The first name in an enum has value 0, the next has value of 1. */
enum boolean {NO, YES};

enum escapes {BELL = '\a', BACKSPACE = '\b', TAB = '\t', NEWLINE = '\n', VTAB = '\v', RETURN = '\r'};

/* If there are no more values specified than the last one,
 * unspecified values continue the progression from the last
 * specfified value.
 */
enum months {JAN = 1, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, DEC};
```

<br>

# Declarations

<br>

# Arithmetic Operations
```c

```

<br>

# Bitwise Operators

| Operator | Desc |
| --- | --- |
| & | bitwise AND. Usually is used to mask off some set of bits |
| \| | bitwise inclusive OR. Used to turn bits on. |
| ^ | bitwise exclusive OR (XOR). Sets a one in each bit position that it's operands have different bits, and zero where they are the same. |
| >> | left shift. Performs left shift by the given by the number of of bit positions given by the right operand.  |
| << | right shift |
| ~ | bitwise NOT. one's complement (unary). Converts each 1-bit into a 0-bit and vice versa. |

Demonstration:
```c
#include <stdio.h>

int main() {
    /* a = 5(00000101), b = 9(00001001) */
    unsigned char a = 5, b = 9;

    printf("a = %d, b = %d\n", a, b);
    
    printf("a&b = %d\n", a & b);
    /* (1)   00000001 */

    printf("a|b = %d\n", a | b);
    /* (13)  00001101 */

    printf("a^b = %d\n", a ^ b);
    /* (12)  0001100 */

    printf("~a = %d\n", ~a);
    /* (250) 11111010 */

    printf("b<<1 = %d\n", b << 1);
    /* (18)  00010010 */

    printf("b>>1 = %d\n", b >> 1);
    /* (4)   00000100 */

    return 0;
}
```

See [this](https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/) for more info.

# Bitwise Facts
Note: Almost all of this part is taken from [this](https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/).

- **The left shift and right shift operators should not be used for negative numbers.** If any of the operands is a negative number, it results in undefined behaviour.

- **If the number is shifted more than the size of integer, the behaviour is undefined.** For example, 1 << 33 is undefined if integers are stored using 32 bits. See *[this](https://wiki.sei.cmu.edu/confluence/display/c/INT34-C.+Do+not+shift+an+expression+by+a+negative+number+of+bits+or+by+greater+than+or+equal+to+the+number+of+bits+that+exist+in+the+operand)* for more details.

- **The bitwise XOR operator is the most useful operator from technical interview perspective.**
  - An example: 
    ```c
    /* Given a set of numbers where all elements occur even number of
     * times except one number, find the odd occurring number
    */
    #include <stdio.h> 
      
    /* Function to return the only odd occurring element */
    int findOdd(int arr[], int n)
    {
        int res = 0, i;
        for (i = 0; i < n; i++)
            res ^= arr[i];
        return res;
    }
    
    int main(void) {
        int arr[] = { 12, 12, 14, 90, 14, 14, 14 };
        int n = sizeof(arr) / sizeof(arr[0]);
        printf("The odd occurring element is %d ",
               findOdd(arr, n));
        return 0;
    }
    ```

- **The bitwise operations should not e used in place of logical operators.** The result of logical operators (&&, || and !) is either 0 or 1, but bitwise operators return an integer value.

- **The left-shift and right-shift operators are equivalent to multiplication and division by 2 respectively.**

- **The & operator can be used to check if a number is odd or even.**
  - ```c
    #include <stdio.h>

    int main() {
        int x = 19;
        (x & 1) ? printf("odd") : printf("even");
        return 0;
    }

    /* Output : odd */
    ```

- **The result of ~ operator on a small number can be a big number if the result is stored in an unsigned variable.** And the result maybe a negative number if the result is stored in a signed variable.

<br>

# Bits Manipulation
See [this](https://www.geeksforgeeks.org/bits-manipulation-important-tactics/). Cool stuff.

<br>

# Bitwise Hacks & Tricks

See [this](https://www.geeksforgeeks.org/bitwise-hacks-for-competitive-programming/). Also [this](https://www.geeksforgeeks.org/bit-tricks-competitive-programming/).

<br>

# If & Else If & Else Statement

```
if (expression) {
    statement;
} else if (expression) {
    statement;
} else {
    statement;
}
```
If an expression is true, the *statement* gets executed, then the chain gets terminated.

<br>

# Switch Statement



<br><br><br><br><br><br><br>

### What to do?

```
- [ ] Dynamic array implementation [O(N)] (Make it a library?)
- [ ]

```