**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 24th February 2022

## Problem Statement:
Given the head of a linked list, return the list after sorting it in **ascending order**.

## Approach:
Perform merge sort

**Note:** If the array is even, we need the first element, hence start the fast pointer with head->next

## Solution: 
```cpp
// Linked List
// Time: O(nlogn)
// Space: O(1) + O(logn) -> Stack space

class Solution {
public:
    
    ListNode* merge(ListNode *left, ListNode *right){
        ListNode *ans = new ListNode(0);
        ListNode *temp = ans;
        
        while(left && right){
            if(left->val < right->val){
                temp->next = left;
                left = left->next;
            }
            else{
                temp->next = right;
                right = right->next;
            }
            temp = temp->next;
        }
        
        // No need to iterate because we're joining the first element 
        // and remaining elements are linked to it.
        if(left){
            temp->next = left;
        }
        
        if(right){
            temp->next = right;
        }
        
        return ans->next;
    }

    // Divide list into two parts
    // 1. Head -> Start to middle
    // 2. otherHalf -> Middle+1 to end

    ListNode* sortList(ListNode* head) {
        // Zero or one element
        if(!head || !head->next)
            return head;

        // Find the middle of the node
        ListNode *slow = head;
        ListNode *fast = head->next;
        
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;
        }
        
        ListNode *otherHalf = slow->next;
        // Breaking the list by pointing the next of the middle to NULL
        slow->next = NULL;
        
        return merge(sortList(head), sortList(otherHalf));
    }
};

```
