---
day: 4
title: "Arrays in C"
description: "Covering Single-dimensional Arrays, Accessing Elements, and Basic Operations"
---

# Day 4 - Arrays in C

## Activity Problems  
1. [Find sum of elements in an array dynamically](https://www.hackerrank.com/challenges/1d-arrays-in-c/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <stdlib.h>

int main() 
{
    int n;
    scanf("%d", &n);

    // Create a dynamic array of size n
    int arr[n];

    // Read the values from stdin and store them in the array
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    // Calculate the sum of all elements in the array
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += arr[i];
    }

    // Print the sum
    printf("%d\n", sum);

    return 0;
}
```
2. [Reversing the array](https://www.hackerrank.com/challenges/reverse-array-c/problem?isFullScreen=true)
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int num, *arr, i;
    scanf("%d", &num);
    arr = (int*) malloc(num * sizeof(int));
    for(i = 0; i < num; i++) {
        scanf("%d", arr + i);
    }

    // Swapping left and right positions
    for(i = 0; i < num/2; i++) {
       int temp = arr[i];
       arr[i] = arr[num-1-i];
       arr[num-1-i] = temp;
    }

    for(i = 0; i < num; i++)
        printf("%d ", *(arr + i));
    return 0;
}
```
3. [Remove duplicates from an array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
```c
int removeDuplicates(int* nums, int numsSize) {
    int j = 1;
    for(int i = 1; i < numsSize; i++){
        if(nums[i] != nums[i - 1]){
            nums[j] = nums[i];
            j++;
        }
    }
    return j;
}
```
4. [Search insert position](https://leetcode.com/problems/search-insert-position/description/)
```c
int searchInsert(int* nums, int numsSize, int target) {
    int l =0, r= numsSize-1;
    while(l<=r){
        int mid = (l+r)/2;
        if (nums[mid] == target)
            return mid;
        else if(nums[mid] < target)
            l = mid+1;
        else
            r = mid-1;
    }
    return l;
}
```
5. [Plus one](https://leetcode.com/problems/plus-one/description/)
```c
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int s = 1;
    int i;
    // Please give the malloc() related statements to the student. The test will not pass otherwise.
    int* p;
    p = (int *) malloc(sizeof(int)*(digitsSize+1));
    if(p == NULL) return NULL;

    i = digitsSize - 1;
    while (i >= 0) {
        p[i] = (digits[i] + s) % 10;
        s = (digits[i] + s) / 10;
        i--;
    }
    if (s) {
        for(int i=digitsSize; i>0; i--)
            p[i] = p[i-1];
        p[0] = 1;
        *returnSize = digitsSize + 1;
    } else {
        *returnSize = digitsSize;
    }
    return p;
}
```
6.  [Player Height](https://www.codechef.com/problems/DOLL?tab=statement)
```c
#include <stdio.h>

int func(int a[],int k,int n){
    int c=0;
    for (int i=0;i<n;i++){
        if (a[i]>k){
            c +=1;
        }
    }
    return c;
}
int main(void) {
    int t;
    scanf("%d",&t);
    while(t--){
        int n,k;
        int i;
        scanf("%d %d",&n,&k);
        int a[n];
        for (i=0;i<n;i++){
            scanf("%d",&a[i]);
        }
        int result = func(a,k,n);
        printf("%d\n",result);
    }
    return 0;
}
```
7.  [Sum of 2 least number in array](https://www.codewars.com/kata/558fc85d8fd1938afb000014)
```c
#include <stddef.h>

long sum_two_smallest_numbers(size_t n, const int numbers[n]) {

  long min1, min2; 
  if(numbers[0] < numbers[1]){
    min1 = numbers[0];
    min2 = numbers[1];
  }else{
    min1 = numbers[1];
    min2 = numbers[0];
  }
  
  for(int i=2; i<n; i++){
    if(numbers[i]<min1){
      min2 = min1;
      min1 = numbers[i];
    }else if(numbers[i]<min2){
      min2 = numbers[i];
    }
  }
  
  return min1+min2;
}
```
8.  [Positive-Negative](https://www.interviewbit.com/problems/positive-negative/)
```c
int* solve(int* A, int n1, int *len1) {
    int poscount = 0, negcount = 0;
    *len1 = 2;
    int* result = (int *) malloc(sizeof(int) * (*len1));
    int i = 0;
    for(i=0; i<n1; i++){
        if(A[i]>0)
            poscount += 1;
        if(A[i]<0)
            negcount += 1;
    }
    result[0] = poscount;
    result[1] = negcount;
    return result;
}
```
9.  [Starting Address](https://www.geeksforgeeks.org/questions/isro-isro-cs-2009-question-28/)
```c
// Answer: 1264
Explanation :
Start address of the element = base address of array + number of elements * size of each element = 1120 + 48 * 3 = 1264 
So, option (C) is correct.
```