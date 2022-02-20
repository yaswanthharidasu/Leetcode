# [1288. Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 20th February 2022

## Problem Statement:
Given an array intervals where intervals[i] represent [li, ri), remove all intervals that are covered by another interval in the list.

The interval [a, b) is covered by the interval [c, d) if and only if c <= a and b <= d.

**Return the number of remaining intervals.**

**Example:** <br>
**Input:** intervals =  [[1,4],[3,6],[2,8]] <br>
**Output:** 2

## Approach:

Sort the intervals and check whether the current interval is covered by the preivous interval or not.

## Solution: 
```cpp
// Sorting
// Time: O(nlogn)
// Space: O(n)

class Solution {
public:
    int removeCoveredIntervals(vector<vector<int>>& intervals) {
        // Sorting the intervals 
        sort(intervals.begin(), intervals.end());
        
        // Stores the interval
        vector<int> previous;
        
        // Storing the first interval
        previous.push_back(intervals[0][0]);
        previous.push_back(intervals[0][1]);
        
        // There'll be atleast one interval in the final answer
        int remaining = 1;
        
        for(int i=1; i<intervals.size(); i++){
            // Storing the current interval
            vector<int> current = {intervals[i][0], intervals[i][1]};
            
            // Current interval is covered by the previous interval
            // Ex: previous = [1,6], current = [3,5] ==> Final: [1,6]
            if(current[1] <= previous[1]){
                continue;
            }
            
            // Previous interval is covered by the current interval
            // Ex: previous = [1,5], current = [1,6] ==> Final: [1,6]
            if(current[0] == previous[0] && current[1] > previous[1]){
                previous[1] = current[1];
                continue;
            }
            
            // Other conditions
            remaining++;
            
            // Updating the previous interval with current interval
            previous[0] = current[0];
            previous[1] = current[1];
        }
        return remaining;
    }
};
```