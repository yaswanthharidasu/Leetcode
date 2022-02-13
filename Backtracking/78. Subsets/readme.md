# [78. Subsets](https://leetcode.com/problems/subsets/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 13th February 2022


## Problem Statement:
Given an integer array nums of **unique** elements, return all possible subsets (the power set).

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

**Constraint:** <br>
1 <= nums.length <= 10


## Approach: 
As no.of elements are too less (<10), we can directly use the backtracking approach.

## Solution 1:
```cpp
// Backtracking
// Time: O(2^n*n) -> For each push, it takes O(n)
// Space: O(2^n) + O(n) -> Stack space

class Solution {
public:

    // Storing all possible subsets
    vector<vector<int>> result;

    void recursive(int i, vector<int>& nums, vector<int>& curr) {
        // There are no elements to process
        if (i == nums.size()) {
            result.push_back(curr);
            return;
        }

        // Exclude the element
        recursive(i + 1, nums, curr);

        // Include the element
        curr.push_back(nums[i]);
        recursive(i + 1, nums, curr);
        curr.pop_back();
    }

    vector<vector<int>> subsets(vector<int>& nums) {
        vector<int> curr;
        recursive(0, nums, curr);
        return result;
    }
};
```

## Solution 2: 

```cpp
class Solution {
public:

    // Storing all possible subsets
    vector<vector<int>> result;

    void iterative(int ind, vector<int>& nums, vector<int>& curr) {
        // Pushing as we go deeper
        result.push_back(curr);
        for (int i = ind; i < nums.size(); i++) {
            // Include the element
            curr.push_back(nums[i]);
            iterative(i + 1, nums, curr);
            curr.pop_back();
        }
    }

    vector<vector<int>> subsets(vector<int>& nums) {
        vector<int> curr;
        iterative(0, nums, curr);
        return result;
    }
};
```