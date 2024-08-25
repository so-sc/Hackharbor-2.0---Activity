---
day: 7
title: "Structures and unions"
description: "Covering Structures and Unions, definiton,declaration, usage and their differences"
---
# Day 7 - Structures and Unions

## Activity Problems  
1. [TOO HIGH BOXES](https://www.hackerrank.com/challenges/too-high-boxes/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <stdlib.h>
#define MAX_HEIGHT 41
struct box
{
    int length,width,height;
};

typedef struct box box;

int get_volume(box b) {
    return b.length*b.width*b.height;
}

int is_lower_than_max_height(box b) {
    return b.height<MAX_HEIGHT;
}

int main()
{
	int n;
	scanf("%d", &n);
	box *boxes = malloc(n * sizeof(box));
	for (int i = 0; i < n; i++) {
		scanf("%d%d%d", &boxes[i].length, &boxes[i].width, &boxes[i].height);
	}
	for (int i = 0; i < n; i++) {
		if (is_lower_than_max_height(boxes[i])) {
			printf("%d\n", get_volume(boxes[i]));
		}
	}
	return 0;
}
```
2. [Small-large triangle](https://www.hackerrank.com/challenges/small-triangles-large-triangles/problem)
```c

float calca(triangle t);
void sort_by_area(triangle* tr, int n) {
	for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(calca(tr[i])>calca(tr[j])){
                triangle temp=tr[i];
                tr[i]=tr[j];
                tr[j]=temp;
            }
        }
    }
}

float calca(triangle t){
    float sp=(t.a+t.b+t.c)/2.0;
    float ar=sqrt(sp*(sp-t.a)*(sp-t.b)*(sp-t.c));
    return ar;
}
```
3. [Guess the Output -I](https://www.geeksforgeeks.org/questions/c-structure-union-question-1/)
```
Answer: Compiler Error
```
4. [Guess the Output -II](https://www.geeksforgeeks.org/questions/c-c-quiz-112-question-1/)
```
Answer: No compile error and it’ll print 1 0 2 0
```
5. [Guess the Output - III](https://www.geeksforgeeks.org/questions/c-c-quiz-112-question-3/)
```c
Answer: No compile error and two elements of arr[] would be defined and initialized. Output would be “1 0 1 and 2 0 2”.
```
6. [Guess the Output -IV](https://www.geeksforgeeks.org/questions/c-c-quiz-112-question-4/)
```c
Answer: No compile error and it’ll print 100 A.
```