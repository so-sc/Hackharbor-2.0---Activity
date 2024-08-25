---
day: 1
title: "Refresher to C programming"
description: "History of C, basic syntax, hello-world, operators and expressions"
---

# Day 1 - Refresher to C Programming

## Activity Problems  
1. [Hello World in C](https://www.hackerrank.com/challenges/hello-world-c/problem)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() 
{	
    char s[100];
    scanf("%[^\n]%*c", &s);
    printf("Hello, World!\n%s",s);    
    return 0;
}
```
2. [Playing with characters](https://www.hackerrank.com/challenges/playing-with-characters/problem)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() 
{	
    char ch, s[100], t[100];
    scanf("%c %s %[^\n]%*c", &ch, s, t);
    printf("%c\n%s\n%s", ch, s, t);
    return 0;
}
```
3. [Sum and Diff of two numbers](https://www.hackerrank.com/challenges/sum-numbers-c/problem)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() 
{	
    int a,b;
    float c,d;
    scanf("%d%d",&a,&b);
    scanf("%f%f",&c,&d);
    printf("%d %d\n",a+b,a-b);
    printf("%.1f %.1f",c+d,c-d);
    return 0;
}
```
4. [Division Anomaly](https://www.codechef.com/practice/course/c/LPCAS01/problems/LCAS02)
```c
//Answer: 2
```
5. [Modulo Game](https://www.codechef.com/practice/course/c/LPCAS01/problems/LCAS08)
```c
//Answer: 1
```
6. [Increment Operator](https://www.geeksforgeeks.org/questions/c-operators-question-24/)
```c
//Answer: 13 12
```
7. [Temperature Converter](https://www.codechef.com/practice/course/c/LPCAS03/problems/LCAS30B)
```c
#include <stdio.h>

int main() {
    float fahrenheit = 98.3;
    float cel=(fahrenheit-32)*5/9;
    printf("%f",cel);
    
    return 0;
}

```
8. [Assignment Operator](https://www.codechef.com/learn/course/c/LBCL07A/problems/PPSC29)
```c
/*
Answer: 3

Explanation:
In the given code, the expression a = b assigns the value of b to a and also returns the assigned value. Therefore, the printf() function will print the value of b.*/
```
8. [Total prize money (debug the code)](https://www.codechef.com/learn/course/c-beginner-v2-p1/BC01BC05_V2/problems/BMCP10)
```c
//debug the code challenge
//correct this line
prize_11to100 = 90*Y;
```
10. [Ternary Operator](https://www.codechef.com/learn/course/c/LBCL07A/problems/PPSC27D)
```c
/*
Correct Answer(s):

x < y ? y : x
x >= y ? x : y
x <= y ? y : x
Explanation:
All these conditional statement returns the larger of the two values x and y.
*/
```