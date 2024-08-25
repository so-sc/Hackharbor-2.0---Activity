---
day: 5
title: "Strings and Pointers"
description: "Covering String declaration, String handling functions, Pointer definiton, declaration,usage and pointer arithmetic"
---

# Day 5 - Strings and Pointers in C

## Strings in C

## Activity Problems  
1. [Guess the output](https://www.geeksforgeeks.org/questions/c-string-question-13/)
```
Answer: Nothing is printed on the screen
```
2. [Wordle](https://www.codechef.com/problems/WORDLE)
```c
#include <stdio.h>
int main(void) {
    int t;
    scanf("%d",&t);
    while(t--){
        char s[6],tw[6],res[6];
        scanf("%s",s);
        scanf("%s",tw);
        for(int i=0;i<5;i++) if(s[i]==tw[i]) res[i]='G'; else res[i]='B';
        res[5]='\0';
        printf("%s\n",res);
    }
}
```
3. [Simple Pointer Question](https://www.hackerrank.com/challenges/pointer-in-c/problem?isFullScreen=true)
```c
#include <stdio.h>
void update(int *a,int *b) {
    int t=*a;
    *a=*a+*b;
    *b=((t-*b)>=0)? t-*b: *b-t; 
}
int main() {
    int a, b;
    int *pa = &a, *pb = &b;   
    scanf("%d %d", &a, &b);
    update(pa, pb);
    printf("%d\n%d", a, b);
    return 0;
}
```
4. [Add Binary Strings](https://www.interviewbit.com/problems/add-binary-strings/)
```c
int pwr(int b,int p){
    int res=1;
    while(p--) res*=b;
    return res;
}
int bitcount(int n){
    if(n==0) return 0;
    return 1+bitcount(n/2);
}
char* addBinary(char* A, char* B) {
    int n1=0,n2=0;
    int l1=strlen(A),l2=strlen(B);
    int i;
    for(i=l1-1;i>=0;i--) if(A[i]=='1')n1+=pwr(2,l1-i-1);
    for(i=l2-1;i>=0;i--) if(B[i]=='1')n2+=pwr(2,l2-i-1);
    int sum=n1+n2,rlen=bitcount(sum);
    char* res = (char*)malloc((rlen + 1) * sizeof(char)); int k=0;
    while(sum!=0){
        int r=sum%2;
        res[rlen-1-k]=(char)(r+'0');
        sum/=2;k++;
    }
    res[rlen]='\0';
    return res;
}

```
5. [Printing tokens](https://www.hackerrank.com/challenges/printing-tokens-/problem?isFullScreen=true )
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
int main() {

    char *s;
    s = malloc(1024 * sizeof(char));
    scanf("%[^\n]", s);
    s = realloc(s, strlen(s) + 1);
    int n=strlen(s);
    for(int i=0;i<n;i++) if(s[i]==' ') printf("\n"); else printf("%c",s[i]);
    return 0;
}
```
6. [The Block game](https://www.codechef.com/problems/PALL01 )
```c
#include <stdio.h>
int rev(int n){
    int sum=0;
    while(n!=0){
        sum=sum*10+(n%10);
        n/=10;
    }
    return sum;
}
int main(void) {
    int t;
    scanf("%d",&t);
    while(t--){
        int n;
        scanf("%d",&n);
        if(n==rev(n)) printf("wins\n"); else printf("loses\n");
    }
}
```
7. [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
```c
bool isV(char c){
    return c>='a'&&c<'z'||c>='0'&&c<='9'||c>='A'&&c<'Z';
}
bool isPalindrome(char* s) {
    int n=strlen(s);
    char res[n]; int k=0;
    for(int i=0;i<n;i++){
    if(isV(s[i])){
        if(s[i]>='A'&&s[i]<='Z') s[i]+=32;
        res[k++]=s[i];
    }
    }
    for(int i=0;i<k/2;i++) if(res[i]!=res[k-i-1]) return false;
    return true;
}
```
8. [Process the String](https://www.codechef.com/problems/KOL15A)
```c
#include <stdio.h>
int main(void) {
    int t;char s[1000];
    int sum;
    scanf("%d",&t);
    while(t--){
    sum=0;
    scanf("%s",s);
    int n=strlen(s);
    for(int i=0;i<n;i++) if(s[i]>='0'&&s[i]<='9') sum+=(s[i]-'0');
    printf("%d\n",sum);
}
}
```
9. [Easy Pronunciation ](https://www.codechef.com/problems/EZSPEAK)
```c
#include <stdio.h>
int isV(char c){
    return c=='a'||c=='e'||c=='i'||c=='o'||c=='u';
}
int main(void) {
	int t;
	scanf("%d",&t);
	while(t--){
	    int nl;
	    scanf("%d",&nl);
	    char s[nl];
	    scanf("%s",s);
	    int cc=0,f=0;
	    for(int i=0;i<nl;i++){
	        if(isV(s[i])) cc=0;
	        else{
	            cc++;
	            if(cc==4) {f=1;break;}
	        }
	    }
	    if(f==0) printf("YES\n");
	    else printf("NO\n");
	}

}
```
10. [Rearrange digits](https://www.codechef.com/problems/DIGARR)
```c
#include <stdio.h>
int main(void) {
	int t;
	scanf("%d",&t);
	while(t--){
	 int n;
	 scanf("%d",&n);
	 int f=0,t=0;
	 char s[n];
	 scanf("%s",s);
	 for(int i=0;i<n;i++){
	     if(s[i]=='5'||s[i]=='0') {f=1;break;}
	 }
	 if(f)printf("Yes\n");
	 else printf("No\n");
}
}
```