# [216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 17th February 2022

## Problem Statement:
Find all valid combinations of 'k' numbers that **sum up to target** such that the following conditions are true:

- Only numbers 1 through 9 are used.
- Each number is used at most once.
  
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

**Constraints:** <br>
2 <= k <= 9 <br>
1 <= target <= 60

**Example:** <br>
**Input:** k = 3, n = 9 <br>
**Output:** [[1,2,6],[1,3,5],[2,3,4]]

## Approach:
This is similar to Combination Sum problem, but in this problem, array nums is given **indirectly** (provided only 1 to 9 numbers are used) .i.e. nums = [1,2,3,4,5,6,7,8,9]

As the array size and target are small, we can directly use backtracking approach.


## Solution 1: 
```cpp
// Backtracking
// Time: O(n*2^n)
// Space: O(x*k)
// x = no.of combinations

class Solution {
public:
    vector<vector<int>> result;
    
    void recursive(int i, int len, int sum, vector<int> &curr, vector<int> &nums){
        // Target obtained with k numbers
        if(curr.size() == len && sum == 0){
            result.push_back(curr);
            return ;
        }

        // Base case
        if(i == nums.size() || curr.size() > len || sum < ){
            return ;
        }
        
        // Exclude the number
        recursive(i+1, len, sum, curr, nums);
        
        // Include the number
        curr.push_back(nums[i]);
        sum -= nums[i];
        recursive(i+1, len, sum, curr, nums);
        curr.pop_back();
        sum += nums[i];
    }
    
    vector<vector<int>> combinationSum3(int k, int n) {
        // Creating the nums array
        vector<int> nums = {1,2,3,4,5,6,7,8,9};
        vector<int> curr;
        recursive(0, k, n, curr, nums);
        return result;
    }
};
```

## Solution 2: 
```cpp
// Backtracking
// Time: O(n*2^n)
// Space: O(x*k)
// x = no.of combinations

class Solution {
public:
    vector<vector<int>> result;
    
    void iterative(int ind, int len, int sum ,vector<int> &curr, vector<int> &nums){
        // Target obtained with k numbers
        if(curr.size() == len && sum == 0){
            result.push_back(curr);
            return ;
        }

        // Base cases
        if(curr.size() > len || sum < 0){
            return ;
        }
        
        for(int i=ind; i<nums.size(); i++){
            // Include the number
            curr.push_back(nums[i]);
            sum -= nums[i];
            iterative(i+1, len, sum, curr, nums);
            curr.pop_back();
            sum += nums[i];
        }
    }
    
    vector<vector<int>> combinationSum3(int k, int n) {
        // Creating the nums array
        vector<int> nums = {1,2,3,4,5,6,7,8,9};
        vector<int> curr;
        iterative(0, k, n, curr, nums);
        return result;
    }
};
```