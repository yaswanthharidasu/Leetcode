# [740. Delete and Earn](https://leetcode.com/problems/delete-and-earn/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 5th March 2022

## Problem Statement:
You are given an integer array nums. You want to maximize the number of points you get by performing the following operation any number of times:
- Pick any nums[i] and delete it to earn nums[i] points. Afterwards, you must delete **every** element equal to nums[i] - 1 and **every** element equal to nums[i] + 1.
  
Return the **maximum number of points** you can earn by applying the above operation some number of times.

**Example:** <br>
**Input:** nums = [2,2,3,3,3,4] <br>
**Output: 9**
## Approach:
Convert the problem into House robbery problem.

## Solution: 
```cpp
// Dynamic Programming
// Time: O(n)
// Space: O(n)
class Solution {
public:
    int deleteAndEarn(vector<int>& nums) {
        vector<int> freq(10001, 0);
        // Adding that element at its location
        for(int i=0; i<nums.size(); i++){
            freq[nums[i]]+= nums[i];
        }
        vector<int> dp(10001, 0);
        dp[1] = freq[1];

        // Now, in the frequency array, we cannot select consecutive elements.
        for(int i=2; i<10001; i++){
            dp[i] = max(freq[i]+dp[i-2], dp[i-1]);
        }
        return dp.back();
    }
};
```