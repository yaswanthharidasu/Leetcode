# [90. Subsets II](https://leetcode.com/problems/subsets-ii/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 13th February 2022

## Problem Statement:
Given an integer array nums that **may contain duplicates**, return all possible subsets (the power set).

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

**Constraint:** <br>
1 <= nums.length <= 10

## Solution 1:
```cpp
// Backtracking
// Time: O(2^n*n) -> For each push, it takes O(n)
// Space: O(2^n) + O(n) -> Stack space

class Solution {
public:
    
    // Storing all possible subsets
    vector<vector<int>> result;
    
    void iterative(int ind, vector<int> &nums, vector<int> &curr){
        // Pusing as we go deeper
        result.push_back(curr);
        for(int i=ind; i<nums.size(); i++){
            // As array may contain duplicates, no need to process the same element again
            if(i>ind && nums[i] == nums[i-1])
                continue;
            // Include the element
            curr.push_back(nums[i]);
            iterative(i+1, nums, curr);
            curr.pop_back();
        }
    }
    
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<int> curr;
        // Sorting the elements to avoid processing duplicate elements
        sort(nums.begin(), nums.end());
        iterative(0, nums, curr);
        return result;
    }
};
```