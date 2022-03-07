# [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 7th March 2022

## Problem Statement:
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list and return the head of the merged linked list.


**Example:** <br>
**Input:** list1 = [1,2,4], list2 = [1,3,4]<br>
**Output:** [1,1,2,3,4,4]

## Solution: 
```cpp
// Linked List
// Time: O(n)
// Space: O(n)

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode *result = new ListNode(0);
        ListNode *temp = result;
        
        while(list1 != NULL && list2 != NULL){
            if(list1->val <= list2->val){
                result->next = new ListNode(list1->val);
                list1 = list1->next;
            }
            else{
                result->next = new ListNode(list2->val);
                list2 = list2->next;
            }
            result = result->next;
        }
        
        if(list1 != NULL){
            result->next = list1;
        }
        
        if(list2 != NULL){
            result->next = list2;
        }
        
        return temp->next;
    }
};

```
