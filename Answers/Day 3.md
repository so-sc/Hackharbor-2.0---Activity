---
day: 3
title: "Function Basics"
description: "Covering Function Definition, Declaration, and Calling Functions"
---

## Activity Problems  
1. [Factorial of a number](https://www.hackerrank.com/contests/c-programming-test/challenges/finding-factorial-of-n-number/problem)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
  
    int n,fact=1;
    scanf("%d",&n);
    for(int i=1;i<=n;i++)fact*=i;
    printf("%d",fact);
    return 0;
}

```
2. [Functions in C](https://www.hackerrank.com/challenges/functions-in-c/problem)
```c
#include <stdio.h>

int max_of_four(int a, int b, int c, int d){
     a=(a>b)?a:b;
     c=(c>d)?c:d;
     a=(a>c)?a:c;
     return a;
}

int main() {
    int a, b, c, d;
    scanf("%d %d %d %d", &a, &b, &c, &d);
    int ans = max_of_four(a, b, c, d);
    printf("%d", ans);
    
    return 0;
}
```
3. [Compute Square and Cube](https://www.codechef.com/learn/course/c/LTCCL27/problems/CLFUNC01)
```c
#include <stdio.h>
void sqac(int n){
    printf("%d\n%d\n",n*n,n*n*n);
}
int main(void) {
	int a = 2;
	int b = 3;
	int c = 4;
	sqac(a);sqac(b);sqac(c);
	
}
```
4. [Calling a function witin a function](https://www.codechef.com/learn/course/c/LTCCL27/problems/CLFUNC08)
```c
#include <stdio.h>

// Function to calculate the square of a number
int square(int a) {
    return a * a;
}

// Function to calcuate (a - b) ^ 2
int aMinusBSquare(int a, int b) {
    return square(a-b);
    
}

int main() {
    int result = aMinusBSquare(2, 1);
    printf("Result: %d\n", result);
}
```
5. [Nth Fibonacci number](https://www.naukri.com/code360/problems/nth-fibonacci-number_1115780)
```c
#include <bits/stdc++.h> 
int fibonacciNumber(int n){
    if(n==1||n==2) return 1;
    else if(n==0) return 0;
    long long int f=1,s=1,r=0,i=2;
    while(i++<n){
        r=(s+f) % 1000000007;
        f=s;
        s=r;
    }
    return r;
}
```
6. [Max of four](https://www.hackerrank.com/challenges/functions-in-c/problem?isFullScreen=true)
```c
#include <stdio.h>

int max_of_four(int a, int b, int c, int d){
     a=(a>b)?a:b;
     c=(c>d)?c:d;
     a=(a>c)?a:c;
     return a;
}

int main() {
    int a, b, c, d;
    scanf("%d %d %d %d", &a, &b, &c, &d);
    int ans = max_of_four(a, b, c, d);
    printf("%d", ans);
    
    return 0;
}
```
7. [Gate CS-2000](https://www.geeksforgeeks.org/questions/gate-gate-cs-2000-question-43/)
```
Answer: 10
```
8. [ISRO-CS'08](https://www.geeksforgeeks.org/questions/isro-isro-cs-2008-question-37/)
```
Answer: 7
```
9. [Bitwise Operators](https://www.hackerrank.com/challenges/bitwise-operators-in-c/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
void calculate_the_maximum(int n, int k) {
    int max1=0,max2=0,max3=0;
  for(int i=1;i<n;i++){
      for(int j=i+1;j<=n;j++){
      int or= i|j;
      int and= i&j;
      int xor = i^j;
      if(or<k&&max1<=or) max1=or;
      if(and<k&&max2<=and) max2=and;
      if(xor<k&&max3<=xor) max3=xor;
  }}
  printf("%d\n%d\n%d",max2,max1,max3);
}
int main() {
    int n, k;
  
    scanf("%d %d", &n, &k);
    calculate_the_maximum(n, k);
 
    return 0;
}
```
10. [Pattern problem](https://www.hackerrank.com/challenges/printing-pattern-2/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() 
{

    int n;
    scanf("%d", &n);
      int a[(n*2)-1][(n*2)-1];
      for(int i=0;i<=((n*2)-1)/2;i++){
          for(int j=0;j<(n*2)-1;j++){
              if(i==0||j==0||j==(n*2)-2||i==(n*2)-2) a[i][j]=n;
              else{
                  if(j>=i&&j<=(n*2)-2-i)a[i][j]=a[i-1][j]-1;
                  else
                  a[i][j]=a[i-1][j];
              }
          }
      }
      
      for(int i=0;i<=((n*2)-1)/2;i++){
          for(int j=0;j<(n*2)-1;j++){
          printf("%d ",a[i][j]);
          }printf("\n");
      }
      for(int i=((n*2)/2)-2;i>=0;i--){
          for(int j=0;j<(n*2)-1;j++){
          printf("%d ",a[i][j]);
          }printf("\n");
      }
    return 0;

}
```