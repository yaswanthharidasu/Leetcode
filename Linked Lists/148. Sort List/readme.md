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
// Space: O(1) + O(n/2) -> Stack space

class Solution {
public:
    
    ListNode* merge(ListNode *list1, ListNode *list2){
        ListNode *ans = new ListNode(0);
        ListNode *temp = ans;
        
        while(list1 && list2){
            if(list1->val < list2->val){
                temp->next = list1;
                list1 = list1->next;
            }
            else{
                temp->next = list2;
                list2 = list2->next;
            }
            temp = temp->next;
        }
        
        // No need to iterate because we're joining the first element 
        // and remaining elements are linked to it.
        if(list1){
            temp->next = list1;
        }
        
        if(list2){
            temp->next = list2;
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
