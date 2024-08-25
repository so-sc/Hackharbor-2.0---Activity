---
day: 9
title: "Data Structures"
description: "Covering Stacks, Queues, Circular Queues, their definitons,operations and implementaion"
---
# Day 9 - Data Structures


## Activity Problems  
1. [Valid Parenthesis](https://www.codechef.com/practice/course/stacks-and-queues/STAQUEF/problems/PREP59)
```c
/*This question can be solved only using the top 
variable (without the stack array). The stack array
is useless here since we are only using one type of 
bracket. I took it just for visualistaion and tracing purposes.*/
#include <stdio.h>
#define ms 100000
char stk[ms];
int top=-1;
int main(void) {
    int t;
    scanf("%d",&t);
	while(t--){
	    int f=1;
	    char s[ms];
	    top=-1;
	    scanf("%s",s);
	    int n=strlen(s);
	    for(int i=0;i<n;i++){
	        if(s[i]=='(') stk[++top]='(';
	        else{
	            if(top<=-1){f=0; break;}
	            top--;
	        }
	    }
	    if(f&&top<0) printf("1\n");
	    else printf("0\n");
	}

}
```
2. [First unique character](https://leetcode.com/problems/first-unique-character-in-a-string/description/)
```c
int firstUniqChar(char* s) {
   int freq[26];//freq map
   for(int i=0;i<26;i++) freq[i]=0;
   int n=strlen(s);
   for(int i=0;i<n;i++) freq[s[i]-'a']++;
   for(int i=0;i<n;i++) if(freq[s[i]-'a']==1) return i;
   return -1;
}
```
3. [Removing stars from a string](https://leetcode.com/problems/removing-stars-from-a-string/)
```c
#define ms 100000
char* removeStars(char* s) {
    char stk[ms];
    int top=-1; 
    int n=strlen(s);
    for(int i=0;i<n;i++)if(s[i]!='*') stk[++top]=s[i]; else if(top>=0) top--;
    char *res=(char*)malloc((top+2)*sizeof(char));
    for(int i=top;i>=0;i--) res[i]=stk[i];
    res[top+1]='\0';
    return res;
}
```

5. [Nearest Smaller number](https://www.interviewbit.com/problems/nearest-smaller-element/)
```c
int* prevSmaller(int* a, int n1, int *len1) {
    int *res =(int*)malloc(n1*sizeof(int));
    *len1=n1;
    int i,j;
    for(i=0;i<n1;i++){
        int rs=-1;
        for(j=i-1;j>=0;j--){
            if(a[j]<a[i]){rs=a[j];break;}
        }
        res[i]=rs;
    }
    return res;
}
```
6. [Stone Pile](https://www.codechef.com/practice/course/stacks-and-queues/STAQUEF/problems/STONE_PILE)
```c
#include <stdio.h>
#include <stdlib.h>

struct Queue {
    int *items;
    int front;
    int rear;
    int size;
    int capacity;
};

struct Queue* createQueue(int capacity) {
    struct Queue* queue = (struct Queue*)malloc(sizeof(struct Queue));
    queue->capacity = capacity;
    queue->front = 0;
    queue->size = 0;
    queue->rear = capacity - 1; // This is important for proper circular behavior
    queue->items = (int*)malloc(queue->capacity * sizeof(int));
    return queue;
}

int isFull(struct Queue* queue) {
    return (queue->size == queue->capacity);
}

int isEmpty(struct Queue* queue) {
    return (queue->size == 0);
}

void enqueue(struct Queue* queue, int item) {
    if (isFull(queue))
        return;
    queue->rear = (queue->rear + 1) % queue->capacity;
    queue->items[queue->rear] = item;
    queue->size = queue->size + 1;
}

int dequeue(struct Queue* queue) {
    if (isEmpty(queue))
        return -1;
    int item = queue->items[queue->front];
    queue->front = (queue->front + 1) % queue->capacity;
    queue->size = queue->size - 1;
    return item;
}

int main() {
    int t, val, n, a, turn;
    scanf("%d", &t);
    while (t--) {
        struct Queue* answer = createQueue(100001);
        scanf("%d", &n);
        turn = 0;
        for (int i = 0; i < n; i++) {
            scanf("%d", &a);
            enqueue(answer, a);
        }
        while (answer->size > 1) {
            if (turn % 2 == 0) {
                val = dequeue(answer);
                enqueue(answer, val);
                dequeue(answer);
            } else {
                val = dequeue(answer);
                enqueue(answer, val);
                val = dequeue(answer);
                enqueue(answer, val);
                dequeue(answer);
            }
            turn++;
        }
        if (n % 2 == 1)
            printf("%d %d\n", 0, answer->items[answer->front]);
        else
            printf("%d %d\n", 1, answer->items[answer->front]);
        dequeue(answer);
        free(answer->items);
        free(answer);
    }
    return 0;
}
```