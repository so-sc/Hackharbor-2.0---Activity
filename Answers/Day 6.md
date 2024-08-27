---
day: 6
title: "Dynamic Memory Allocation"
description: "Covering Dynamic Memory Allocation, Pointer Arithmetic, and Pointer to Pointer"
---

# Day 6 - Dynamic Memory Allocation

## Activity Problems  
1. [Give the most appropriate pair](https://www.geeksforgeeks.org/questions/c-dynamic-memory-allocation-question-1/)
```c
// Answer: X—3 Y—1 Z-2
```
2. [Guess Output 1](https://www.geeksforgeeks.org/questions/c-dynamic-memory-allocation-question-3/)
```c
// Answer: May not work
Explanation :
The program is not valid. Try replacing “int *p;” with “int *p = NULL;” and it will try to dereference a null pointer. This is because fun() makes a copy of the pointer, so when malloc() is called, it is setting the copied pointer to the memory location, not p. p is pointing to random memory before and after the call to fun(), and when you dereference it, it will crash. If you want to add memory to a pointer from a function, you need to pass the address of the pointer (ie. double pointer).
```
3. [Guess Output 2](https://www.geeksforgeeks.org/questions/c-dynamic-memory-allocation-question-2/)
```c
// Answer: Only P1 and P2
Explanation :
In P1, pointer variable x is a local variable to g(), and g() returns pointer to this variable. x may vanish after g() has returned as x exists on stack. So, &x may become invalid. In P2, pointer variable px is being assigned a value without allocating memory to it. P3 works perfectly fine. Memory is allocated to pointer variable px using malloc(). So, px exists on heap, it’s existence will remain in memory even after return of g() as it is on heap.
```
4. [Sparse Arrays](https://www.hackerrank.com/challenges/sparse-arrays/problem?isFullScreen=true)
```c
int* matchingStrings(int stringList_count, char** stringList, int queries_count, char** queries, int* result_count) {
    // Set the result count to be equal to the number of queries
    *result_count = queries_count;
    
    // Allocate memory for the result array
    int* result = (int*)malloc(queries_count * sizeof(int));
    if (result == NULL) {
        printf("Memory allocation failed\n");
        exit(1);
    }
    
    // Initialize all counts to 0
    for (int i = 0; i < queries_count; i++) {
        result[i] = 0;
    }
    
    // Count occurrences of each query string
    for (int i = 0; i < queries_count; i++) {
        for (int j = 0; j < stringList_count; j++) {
            if (strcmp(queries[i], stringList[j]) == 0) {
                result[i]++;
            }
        }
    }
    
    return result;
}
```
