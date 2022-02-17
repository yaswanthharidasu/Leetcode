# [40.Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 17th February 2022

## Problem Statement:
Given an array nums that may contain **duplicates**  and a target, return a list of all **unique combinations** of candidates where the chosen numbers **sum to target**. 

Each number in candidates may only be used **once** in the combination.

**Example:** <br>
**Input:** nums = [10,1,2,7,6,1,5], target = 8 <br>
**Output:** 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]

**Constraint:** <br>
1 <= candidates.length <= 100 <br>
1 <= target <= 30


## Approach:
This is similar to Combination Sum problem, but in this problem, the array might contain duplicates and the each number in nums can be used only once.

As the array size and target are small, we can directly use backtracking approach.


## Solution: 
```cpp
// Backtracking
// Time: O(n*2^n)
// Space: O(x*k)
// x = no.of combinations and k = avg length of each combination

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
            // Avoid processing the same elements again
            if(i != ind && nums[i] == nums[i-1])
                continue;
            // include the element
            curr.push_back(nums[i]);
            target -= nums[i];
            iterative(i+1, target, curr, nums);
            curr.pop_back();
            target += nums[i];
        }
    }
    
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        // Sorting to avoid processing duplicates
        sort(candidates.begin(), candidates.end());
        vector<int> curr;
        iterative(0, target, curr, candidates);
        return result;
    }
};
```