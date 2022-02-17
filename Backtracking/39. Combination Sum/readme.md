# [39. Combination Sum](https://leetcode.com/problems/combination-sum/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 17th February 2022

## Problem Statement:
Given an array of distinct integers candidates and a target integer target, return a list of all **unique combinations** of candidates where the chosen numbers **sum to target**. 

The same number may be chosen from candidates an **unlimited number of times**.

**Constraint:** <br>
1 <= candidates.length <= 30

## Approach:

This is similar to Coin Change 2 problem, but instead of no.of combinations, we need to print the unique combinations.

As the size of array is small (=30), we can directly use backtracking approach.

## Solution 1: 
```cpp
// Backtracking
// Time: O(2^target * k) 
// k = avg length of curr (To push to result)
// Space: O(x*k)
// k = avg length of curr and x = no.of combinations

class Solution {
public:
    vector<vector<int>> result;
    void recursive(int i, int target, vector<int> &curr, vector<int> &nums){
        // Target obtained
        if(target == 0){
            result.push_back(curr);
            // No need to check other numbers
            // As all nums are +ve, if we add one more number, sum will be greater than target
            return ;
        }
        
        // Base cases
        if(target < 0 || i >= nums.size()){
            return ;
        }

        // Exclude the element
        recursive(i+1, target, curr, nums);
        
        // Include the element
        curr.push_back(nums[i]);
        target -= nums[i];
        // Instead of i+1 we use i, because each number can be repeated any no.of times
        recursive(i, target, curr, nums);
        curr.pop_back();
        target += nums[i];
    }

    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<int> curr;
        recursive(0, target, curr, candidates);
        return result;
    }
};
```
## Solution 2: 
```cpp
// Time: O(2^target * k) 
// k = avg length of curr (To push to result)
// Space: O(x*k)
// k = avg length of curr and x = no.of combinations

class Solution {
public:
    vector<vector<int>> result;
    
    void iterative(int ind, int target, vector<int> &curr, vector<int> &nums){
        // Target obtained
        if(target == 0){
            result.push_back(curr);
        }

        // Base case
        if(target < 0){
            return ;
        }

        for(int i=ind; i<nums.size(); i++){
            // Include the element
            target -= nums[i];
            curr.push_back(nums[i]);
            // Instead of i+1, we use i
            iterative(i, target, curr, nums);
            target += nums[i];
            curr.pop_back();
        }
    }

    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<int> curr;
        // recursive(0, target, curr, candidates);
        iterative(0, target, curr, candidates);
        return result;
    }
};
```