# [136. Single Number](https://leetcode.com/problems/single-number/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 15th February 2022

## Problem Statement:
Given a **non-empty** array of integers nums, **_every element appears twice except for one_**. Find that single one.

You must implement a solution with a **linear** runtime complexity and use only **constant** extra space.

**Example:** <br>
**Input:** nums = [4,1,2,1,2] <br>
**Output:** 4

## Approach:
We need to somehow cancel out the repeated numbers, and it finally leads to the non-repeated number.

**Ex:** 4+1+2-1-2 = 4

XOR can be used to cancel the numbers, because a^a = 0

## Solution: 
```cpp
// Bit-Manipulation
// Time: O(n)
// Space: O(1)

class Solution {
public:
    int singleNumber(vector<int>& nums) {
        // If there is only one element, then it is the answer
        int ans = nums[0];
        // Perform XOR of numbers in the array
        for(int i=1; i<nums.size(); i++){
            ans ^= nums[i];
        }
        return ans;
    }
};
```
