---
day: 10
title: "Linked Lists"
description: "Covering Singly Linked Lists, Doubly Linked Lists, and Circular Linked Lists"
---

# Day 10 - Linked Lists

## Activity Problems  
1. [SUBTRACT](https://www.interviewbit.com/problems/subtract/)
```c
listnode* reverse(listnode* head) {
    listnode *prev = NULL, *curr = head, *next = NULL;
    while (curr != NULL) {
        next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}

// Main function to subtract
listnode* subtract(listnode* A) {
    int i;
    if (A == NULL || A->next == NULL)
        return A;

    // Step 1: Find the length of the list
    int length = 0;
    listnode *curr = A;
    while (curr != NULL) {
        length++;
        curr = curr->next;
    }

    // Find the middle node
    int middle = length / 2;
    curr = A;
    for (i = 0; i < middle - 1; i++)
        curr = curr->next;

    // Step 2: Reverse the second half of the list
    listnode *secondHalf = reverse(curr->next);
    curr->next = secondHalf;

    // Step 3: Modify the values of the first half nodes
    listnode *first = A, *second = secondHalf;
    for (i = 0; i < middle; i++) {
        first->val = second->val - first->val;
        first = first->next;
        second = second->next;
    }

    // Step 4: Reverse the second half back
    curr->next = reverse(secondHalf);

    return A;
}
```
2. [ADD TWO NUMBERS AS LL](https://www.interviewbit.com/problems/add-two-numbers-as-lists/)
```c
listnode* addTwoNumbers(listnode* A, listnode* B) {
    listnode* dummyHead = listnode_new(0);
    listnode* curr = dummyHead;
    int carry = 0;

    while (A != NULL || B != NULL) {
        int x = (A != NULL) ? A->val : 0;
        int y = (B != NULL) ? B->val : 0;
        int sum = carry + x + y;
        carry = sum / 10;
        curr->next = listnode_new(sum % 10);
        curr = curr->next;
        if (A != NULL) A = A->next;
        if (B != NULL) B = B->next;
    }

    if (carry > 0) {
        curr->next = listnode_new(carry);
    }

    // Remove the initial zero in the first node
    listnode* result = dummyHead->next;
    free(dummyHead);

    // If the result is all zeros, return a single zero
    if (result == NULL) {
        return listnode_new(0);
    }

    // Reverse the list to check for trailing zeros
    listnode *prev = NULL, *current = result, *next = NULL;
    while (current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    result = prev;

    // Remove trailing zeros
    while (result->next != NULL && result->val == 0) {
        listnode* temp = result;
        result = result->next;
        free(temp);
    }

    // Reverse the list back
    prev = NULL;
    current = result;
    next = NULL;
    while (current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    result = prev;

    return result;
}
```
3. [CONVERT BINARY TO LINKED LIST](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/description/)
```c
int getDecimalValue(struct ListNode* head) {
    int result = 0;
    while (head != NULL) {
        result = (result * 2) + head->val;
        head = head->next;
    }
    return result;
}
```
4. [REMOVE DUPLICATES FROM SORTED LIST](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)
```c
struct ListNode* deleteDuplicates(struct ListNode* head) {
    // If 0 or 1 nodes
    if(head == NULL || head->next == NULL)
        return head;
    
    //If 2 or more nodes
    register struct ListNode *curr = head;
    while(curr != NULL && curr->next != NULL){
        if(curr->val == curr->next->val){
            struct ListNode* temp = curr->next;
            curr->next = temp->next;
            free(temp);
        }else{
            curr = curr->next;
        }
    }
    return head;
}
```
5. [INSERTION SORT USING LIST](https://leetcode.com/problems/insertion-sort-list/description/)
```c
struct ListNode* insertionSortList(struct ListNode* head) {
    if (!head || !head->next) {
        return head;
    }

    struct ListNode* dummy = malloc(sizeof(struct ListNode));
    dummy->next = head;

    struct ListNode* prev = head;
    struct ListNode* cur = head->next;

    while (cur) {
        // already in-order
        if (prev->val <= cur->val) {
            prev = cur;
            cur = cur->next;
        } else {
            struct ListNode* temp = dummy;
            
            while(cur->val > temp->next->val) 
                temp = temp->next;

            // find the stop
            prev->next = cur->next;
            cur->next = temp->next;
            temp->next = cur;

            cur = prev->next;
        }
    }
    return dummy->next;
}
```
6. [COMPARE THE LINKED LIST](https://www.hackerrank.com/challenges/compare-two-linked-lists/problem?isFullScreen=true)
```c
bool compare_lists(SinglyLinkedListNode* head1, SinglyLinkedListNode* head2) {
    if(head1->data==head2->data){
        if(head1->next==head2->next)                    // For NULL pointers and merging lists
            return true;
        else
            return head1->next!=NULL                    // If head1 is shorter return false
            && head2->next!=NULL                        // If head2 is shorter return false
            && compare_lists(head1->next, head2->next); // Moving to next element
    }
    return false;
```
7. [PRINT THE LIST IN REVERSE](https://www.hackerrank.com/challenges/print-the-elements-of-a-linked-list-in-reverse/problem?isFullScreen=true)
```c
void reversePrint(SinglyLinkedListNode* llist) {
    if(llist){
        reversePrint(llist->next);
        printf("%d\n",llist->data);
    }
    return;
}
```
8. [REVERSE A DOUBLY LINKED LIST](https://www.hackerrank.com/challenges/reverse-a-doubly-linked-list/problem?isFullScreen=true)
```c
DoublyLinkedListNode* reverse(DoublyLinkedListNode* llist) {
    if(llist->next==NULL){
        llist->next = llist->prev;
        llist->prev = NULL;
        return llist;
    }else{
        DoublyLinkedListNode* temp = llist->next;
        llist->next = llist->prev;
        llist->prev = temp;
        return reverse(llist->prev);
    }
}
```
9. [INSERT A NODE AT TAIL OF THE LINKED LIST](https://www.hackerrank.com/challenges/insert-a-node-at-the-tail-of-a-linked-list/problem?isFullScreen=true)
```c
SinglyLinkedListNode* insertNodeAtTail(SinglyLinkedListNode* head, int data) {
    SinglyLinkedListNode* newnode = create_singly_linked_list_node(data);
    
    if (head == NULL) {
        return newnode;
    }
    
    SinglyLinkedListNode* current_node = head;
    
    while (current_node->next != NULL) {
        current_node = current_node->next;
    }
    
    current_node->next = newnode;
    
    return head;
}
```
10. [INSERT A NODE AT HEAD OF THE LINKED LIST](https://www.hackerrank.com/challenges/insert-a-node-at-the-head-of-a-linked-list/problem?isFullScreen=true)
```c
SinglyLinkedListNode* insertNodeAtHead(SinglyLinkedListNode* llist, int data) {
    SinglyLinkedListNode* newNode = create_singly_linked_list_node(data);
    newNode->next = llist;
    return newNode;
}
```
11. [INSERT AT A SPECIFIC NODE IN A LINKED LIST](https://www.hackerrank.com/challenges/insert-a-node-at-a-specific-position-in-a-linked-list/problem?isFullScreen=true)
```c
SinglyLinkedListNode* insertNodeAtPosition(SinglyLinkedListNode* llist, int data, int position) {
    SinglyLinkedListNode* newNode = create_singly_linked_list_node(data);
    
    if (position==0) {
        newNode->next = llist;
        llist = newNode;
    }else if (position>0) {
        SinglyLinkedListNode* cur = llist;
        for (int i=1; i<position; i++) {
            cur = cur->next;
        }
        newNode->next = cur->next;
        cur->next = newNode;
    }
    return llist;
}
```
12. [DELETE A NODE](https://www.hackerrank.com/challenges/delete-a-node-from-a-linked-list/problem?isFullScreen=true)
```c
SinglyLinkedListNode* deleteNode(SinglyLinkedListNode* llist, int position) {
    if(position==0){
        SinglyLinkedListNode* temp = llist;
        llist = llist->next;
        free(temp);
    }else if(position>0){
        SinglyLinkedListNode* cur = llist;
        for (int i=1; i<position; i++) {
            cur = cur ->next;
        }
        
        SinglyLinkedListNode* temp = cur->next;
        cur->next = cur->next->next;
        free(temp) ;
    }
    return llist;
}
```