---
day: 2
title: "Control Structures and Functions"
description: "Covering Conditional Statements, Loops, Scope and Lifetime of Variables and Errors"
---

## Activity Problems
1. [Even Sum](https://www.codechef.com/practice/course/c/LPCAS06/problems/CASS27?tab=solution)
```c
#include <stdio.h>

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    int sum = a + b;
    if(sum % 2 == 0)
        printf("YES");
    else 
        printf("NO");
    return 0;
}
```
2. [Triangle Type](https://www.codechef.com/practice/course/c/LPCAS06/problems/CASS28?tab=solution)
```c
#include <stdio.h>

int main() {
    int side1, side2, side3;

    scanf("%d %d %d", &side1, &side2, &side3);

    // Check if the triangle is equilateral
    if (side1 == side2 && side2 == side3) {
        printf("Equilateral");
    }
    // Check if the triangle is isosceles
    else if (side1 == side2 || side2 == side3 || side1 == side3) {
        printf("Isosceles");
    }
    // If none of the above conditions are met, the triangle is scalene
    else {
        printf("Scalene");
    }

    return 0;
}
```
3. [Sum of Digits](https://www.hackerrank.com/challenges/sum-of-digits-of-a-five-digit-number/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
	
    int n, sum = 0;
    scanf("%d", &n);
    while(n){
        int digit = n%10;
        n /= 10;
        sum += digit;
    }
    printf("%d", sum);
}
```
4. [ISRO CS 2011](https://gist.github.com/galaxygamerman/b9bb496865026f9cebdea9a56f3f992d#file-isro-cs-2011-md)
```c
#include 
int main()
{
int index;
for(index=1; index<=5; index++)
{
printf("%d", index);
if (index==3)
continue;
}
}

// Output: 12345
```
5. [ISRO CS 2014](https://gist.github.com/galaxygamerman/b9bb496865026f9cebdea9a56f3f992d#file-isro-cs-2014-md)
```c
// How many lines of output does the following C code produce?
#include<stdio.h>
float i=2.0;
float j=1.0;
float sum = 0.0;
main()
{
    while (i/j > 0.001)
    {
        j+=j;
        sum=sum+(i/j);
        printf("%f\n", sum);
    }
}

//Answer: 11 lines
```
6. [GATE CS 2012](https://gist.github.com/galaxygamerman/b9bb496865026f9cebdea9a56f3f992d#file-gate-cs-2012-md)
```c
// What will be the output of the following C program segment? (GATE CS 2012)
char inchar = 'A';
switch (inchar)
{
case 'A' :
    printf ("Choice A \n") ;
case 'B' :
    printf ("Choice B ") ;
case 'C' :
case 'D' :
case 'E' :
default:
    printf ("No Choice") ;
}

// Output: Choice A Choice B No choice
```
7. [Compile Time Error](https://www.codechef.com/learn/course/c/LBCL07A/problems/PPSC28)
```c
// What will the following code output?
#include <stdio.h>

int main() {
  int a = 5;
  
  printf("%d", !(x > 5 && x < 10));
  return 0;
}
// Output: Compilation error
```
8. [Print the Numbers in Words](https://www.hackerrank.com/challenges/conditional-statements-in-c/problem?isFullScreen=true)
```c
#include <assert.h>
#include <limits.h>
#include <math.h>
#include <stdbool.h>
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* readline();



int main()
{
    char* n_endptr;
    char* n_str = readline();
    int n = strtol(n_str, &n_endptr, 10);

    if (n_endptr == n_str || *n_endptr != '\0') { exit(EXIT_FAILURE); }

    switch (n) {
    case 0: printf("zero"); break;
    case 1: printf("one"); break;
    case 2: printf("two"); break;
    case 3: printf("three"); break;
    case 4: printf("four"); break;
    case 5: printf("five"); break;
    case 6: printf("six"); break;
    case 7: printf("seven"); break;
    case 8: printf("eight"); break;
    case 9: printf("nine"); break;
    default:printf("Greater than 9");
    }

    return 0;
}

char* readline() {
    size_t alloc_length = 1024;
    size_t data_length = 0;
    char* data = malloc(alloc_length);

    while (true) {
        char* cursor = data + data_length;
        char* line = fgets(cursor, alloc_length - data_length, stdin);

        if (!line) { break; }

        data_length += strlen(cursor);

        if (data_length < alloc_length - 1 || data[data_length - 1] == '\n') { break; }

        size_t new_length = alloc_length << 1;
        data = realloc(data, new_length);

        if (!data) { break; }

        alloc_length = new_length;
    }

    if (data[data_length - 1] == '\n') {
        data[data_length - 1] = '\0';
    }

    data = realloc(data, data_length);

    return data;
}
```
9.  [Even or Odd in a range](https://www.hackerrank.com/challenges/for-loop-in-c/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>



int main() 
{
    int a, b;
    scanf("%d\n%d", &a, &b);
  	
    for (int n=a; n<=b; n++) {
        if (n>=1 && n<=9) {
            switch (n) {
                case 0: printf("zero"); break;
                case 1: printf("one"); break;
                case 2: printf("two"); break;
                case 3: printf("three"); break;
                case 4: printf("four"); break;
                case 5: printf("five"); break;
                case 6: printf("six"); break;
                case 7: printf("seven"); break;
                case 8: printf("eight"); break;
                case 9: printf("nine"); break;
                default:printf("Greater than 9");
            }
        }else if (n>9) {
            switch (n%2) {
                case 0: printf("even");break;
                case 1: printf("odd");break;
            }
        }
        printf("\n");
    }

    return 0;
}

// Or a more advanced answer (arrays have not been covered yet)

#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() 
{
    int a, b;
    scanf("%d\n%d", &a, &b);

    // Define the English representations of numbers from 1 to 9
    char* numbers[] = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};

    // Loop through the interval [a, b]
    for (int i = a; i <= b; i++) {
        if (i <= 9) {
            // If i is less than or equal to 9, print its English representation
            printf("%s\n", numbers[i-1]);
        } else if (i % 2 == 0) {
            // If i is even, print "even"
            printf("even\n");
        } else {
            // If i is odd, print "odd"
            printf("odd\n");
        }
    }

    return 0;
}
```
