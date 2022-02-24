# [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 24th February 2022

## Problem Statement:
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the **second middle node**.

## Approach:

Maintain two pointers:
1. **slow** - Move by one step.
2. **fast** - Move by two steps.
   
By the time, fast pointer reaches the end of the list, slow pointer will be at the middle.

## Solution: 
```cpp
// Linked List
// Time: O(n)
// Space: O(1)
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        // Zero or only one node
        if(!head || !head->next){
            return head;
        }
        
        ListNode *slow = head;
        ListNode *fast = head;
        
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;
        }
         
        return slow;
    }
};
```
