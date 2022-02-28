# [228. Summary Ranges](https://leetcode.com/problems/summary-ranges/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 28th February 2022

## Problem Statement:
You are given a **sorted unique** integer array nums.

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:
- "a->b" if a != b
- "a" if a == b

**Example:** <br>
**Input:** nums = [0,1,2,4,5,7] <br>
**Output:**  ["0->2","4->5","7"]

## Solution: 
```cpp
// Ad Hoc
// Time: O(n)
// Space: O(n)
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> ans;
        // No numbers in nums
        if(nums.size() == 0){
            return ans;
        }
        
        // Starting interval in the range
        int start = nums[0];
        
        for(int i=1; i<nums.size(); i++){
            // Ending interval in the range
            int end = nums[i];
            
            // Not a consecutive number
            if(end-1 != nums[i-1]){
                // If start and end interval are same, then just store that number
                // Otherwise store as "start->end"
                if(start == nums[i-1])
                    ans.push_back(to_string(start));
                else
                    ans.push_back(to_string(start) + "->" + to_string(nums[i-1]));
                start = end;
            }
        }
        
        if(start == nums.back())
            ans.push_back(to_string(start));
        else
            ans.push_back(to_string(start) + "->" + to_string(nums.back()));
        
        return ans;
    }
};
```