# [24. Swap Node in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 16th February 2022

## Problem Statement:
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

**Example:** <br>
**Input:** head = [1, 2, 3, 4] <br>
**Output:** [2, 1, 4, 3]

## Approach:
Maintain 3 pointers:
1. Previous Node
2. Current Node
3. Next Node

Swap these pointers as required and move to the next nodes

## Solution: 
```cpp
// Linked List
// Time: O(n)
// Space: O(1)
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        // Zero nodes or only one node
        if(head == NULL || head->next == NULL){
            return head;
        }
    
        ListNode *curr = head; 
        ListNode *prev = NULL;
        
        while(curr && curr->next){
            // Finding the next node
            ListNode *nextNode = curr->next;

            // Swapping pairs
            curr->next = nextNode->next;
            nextNode->next = curr;

            // Executes only for the first time
            if(prev == NULL){
                prev = nextNode;
                head = prev;
            }
            else{
                prev->next = nextNode;
            }

            // Moving to next pair
            prev = curr;
            curr = curr->next;
        }
        return head;
    }
};

```
