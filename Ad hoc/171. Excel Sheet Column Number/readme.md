# [171. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 22nd February 2022

## Problem Statement:
Given a string _columnTitle_ that represents the column title as appear in an Excel sheet, return its corresponding _column number_.

**Example:** <br>
**Input:** columnTitle = "ZY" <br>
**Output:** 701

## Approach:
Kind of Rolling Hash. Find the value of each letter and mulitply with 26 because alphabets are base-26.

## Solution: 
```cpp
// Ad Hoc, math
// Time: O(n)
// Space: O(1)

class Solution {
public:
    int titleToNumber(string columnTitle) {
        int ans = 0;
        for(char ch: columnTitle){
            ans = (ans*26) + (ch-'A'+1);
        }
        return ans;
    }
};
```