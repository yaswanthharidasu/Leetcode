# [168. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/) 
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 13th February 2022

## Problem Statement:
Given an integer _columnNumber_, return its corresponding _column title as_ it appears in an Excel sheet.

**Example:** <br>
**Input:** columnNumber = 701 <br>
**Output:** 701

## Approach:

## Solution 1: 
```cpp
// Ad Hoc, Math
// Time: O(n)
// Space: O(1)
class Solution {
public:
    string convertToTitle(int columnNumber) {
        string ans;
        while(columnNumber != 0){
            int rem = columnNumber%26;
            columnNumber /= 26;
            // For 'Z', we get remainder as zerohence treating it separately and reduce the column number.
            if(rem == 0){
                ans += 'Z';
                columnNumber -= 1;
            }
            else{
                ans += 'A'+(rem-1);
            }
        }
        // Reverse the string formed
        reverse(ans.begin(), ans.end());
        return ans;
    }
};
```

## Solution 2: 
```cpp
// Ad Hoc, Math
// Time: O(n)
// Space: O(1)
class Solution {
public:
    string convertToTitle(int columnNumber) {
        string ans;
        while(columnNumber != 0){
            columnNumber -= 1;
            int rem = columnNumber%26;
            columnNumber /= 26;
            ans += 'A'+rem;
        }
        reverse(ans.begin(), ans.end());
        return ans;
    }
};
```