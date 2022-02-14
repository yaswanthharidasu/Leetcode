# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 14th February 2022

## Problem Statement:
Given the root of a binary tree, return its **maximum depth**.

## Solution: 
```cpp
// Trees
// Time: O(n)
// Space: O(logn) -> Stack space

class Solution {
public:
    
    int maxDepth(TreeNode* root) {
        if(root == NULL)
            return 0;
        // Return max of left and right subtrees 
        return max(maxDepth(root->left), maxDepth(root->right))+1;
    }
    
};
```

