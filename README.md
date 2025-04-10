# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# Register Number : 212222110002
# Date : 10.04.2025
# AIM :
####   To write a C program to implement a symbol table.

# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol and memory address are inserted into the symbol table.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and the symbol table has been checked for the corresponding variable, the variable along with its address is displayed as a result.
8.	Stop the program. 
# PROGRAM
```C
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    char b[MAX_EXPRESSION_SIZE], d[15], c, srch;

    // Array of pointers for storing addresses of symbols.
    void *add[MAX_EXPRESSION_SIZE];

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; // Null terminate the string
    n = i - 1;

    printf("Given Expression: %s\n", b);

    printf("\nSymbol Table\n");
    printf("Symbol\taddr\ttype\n");

    // Iterate through the expression to identify symbols.
    for (j = 0; j <= n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            if (j == n || 
                b[j + 1] == '+' || b[j + 1] == '-' || b[j + 1] == '*' || b[j + 1] == '=' || b[j + 1] == '\0') {
                
                // Store the symbol and its "address".
                add[x] = &b[j];  // Use address of the character in expression.
                d[x] = c;        // Store the symbol itself.
                printf("%c\t%p\tidentifier\n", c, add[x]);
                x++;
            }
        }
    }

    printf("\nThe symbol to be searched: ");
    getchar(); // To consume newline after input prompt.
    srch = getchar();

    // Search for the symbol in the symbol table.
    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c@address%p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (flag == 0)
        printf("Symbol Not Found\n");

    // No need to free anything as we're not dynamically allocating memory for single characters anymore.

    return 0;
}
```
# OUTPUT

### Valid Input

![image](https://github.com/user-attachments/assets/2fcbfa7d-8ac9-47cd-a8e8-08c9268c85bf)

### Invalid Input

![image](https://github.com/user-attachments/assets/e898e9ab-b16c-45a5-b6da-8af3b1b634ee)



# RESULT
### The program to implement a symbol table is executed and the output is verified.
