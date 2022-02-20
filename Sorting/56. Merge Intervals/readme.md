# [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 20th February 2022

## Problem Statement:
Given an array of intervals where _intervals[i] = [start, end]_, merge all overlapping intervals, and **return an array of the non-overlapping intervals** that cover all the intervals in the input.

**Example:** <br>
**Input:** intervals = [[1,3],[2,6],[8,10],[15,18]] <br>
**Output:**  [[1,6],[8,10],[15,18]]

## Approach:

Sort the intervals and check whether an interval is overlapping with the preivous interval not.

## Solution: 
```cpp
// Sorting
// Time: O(nlogn)
// Space: O(n)

class Solution {
public:

    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        vector<vector<int>> result;

        // Sorting the intervals in the increasing order
        sort(intervals.begin(), intervals.end());

        // Storing the first interval in the previous vector
        vector<int> previous = {intervals[0][0], intervals[0][1]};

        for(vector<int> current: intervals){
            // Complete overlap of intervals
            // -----------------------------
            // Ex: prev=[1,5], curr=[2,3] -> Do nothing as the merged interval of these two = [1,5]
            if(current[0] <= previous[1] && current[1] <= previous[1])
                continue;

            // Partial overlap of intervals
            // ----------------------------
            // Ex: prev=[1,3], curr=[2,6] -> Update the right interval of the previous interval = [1, 6]
            else if(current[0] <= previous[1] && current[1] > previous[1]){
                previous[1] = current[1];   
            }

            // No overlap of intervals
            // -----------------------
            // Ex: prev=[1,6] curr=[8,10] then store the previous interval in result
            // And update the previous with current intervals for checking with next intervals
            else{
                result.push_back(previous);
                previous[0] = current[0];
                previous[1] = current[1];
            }
        }
        // Finally push the previous interval in the result
        result.push_back(previous);

        return result;
    }
};
```