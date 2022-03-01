# [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 1st March 2022

## Problem Statement:
Given an integer n, return number of 1's in the binary representation of [0,n]

**Example:** <br>
**Input:** n = 5 <br>
**Output:** [0,1,1,2,1,2]

## Solution 1:
For each number i:
- Calculate no.of bits in it = log(i)
- Iterate over all bits and check whether it is 0 or 1

**Time:** O(nlogn) for n numbers

## Solution 2: 
No.of 1's for 'num' can be calculated as:
- No.of 1's at num/2, if 'num' is even
- No.of 1's at num/2 + 1, if 'num' is odd


```cpp
// Bit manipulation
// Time: O(n)
// Space: O(n)

class Solution {
public:
    vector<int> countBits(int n) {
        // Create a vector of size n+1 and initialize with 0
        vector<int> ans(n+1,0);
        
        for(int i=1; i<n+1; i++){
            // If num is divided by 2, then no.of 1's = no.of 1's at num/2
            if(i%2 == 0){
                ans[i] = ans[i/2];
            }
            // Otherwise, no.of 1's = no.of 1's at num/2+1
            else{
                ans[i] = ans[i/2]+1;
            }
        }
        return ans;
    }
};
```