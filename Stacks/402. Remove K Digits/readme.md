# [402. Remove K Digits](https://leetcode.com/problems/remove-k-digits/)
**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 18th February 2022

## Problem Statement:
Given string num representing a non-negative integer num, and an integer k, return the **smallest possible integer** after removing k digits from num.

**Example 1:** <br>
**Input:** num = "1432219", k = 3 <br>
**Output:** "1219"

**Example 2:** <br>
**Input:** num = "10200", k = 1 <br>
**Output:** "200"

**Constraint:** <br>
1 <= k <= num.length <= 105

## Approach:
As we need to find the smallest integer, stack can be used to store the numbers in the increasing order.

## Solution: 
```cpp
// Monotonic stack
// Time: O(n)
// Space: O(n)

class solution:{
public:
    string removeKdigits(string num, int k) {
        // Maintain the stack in increasing order from bottom to top
        stack<char> st;
        for(int i=0; i<num.size(); i++){
            // Popping elements if greater than current digit and when k>0
            while(!st.empty() && st.top() > num[i] && k>0){
                st.pop();
                k--;
            }
            st.push(num[i]);
        }

        // Ex: "12345", k=3
        // For the above example, while inserting the elements, no element will be popped
        // But we need to remove 'k' characters 
        // Hence remove the top k characters
        while(k!=0){
            st.pop();
            k--;
        }
        
        // Storing stack elements in ans
        string ans;
        while(!st.empty()){
            ans += st.top();
            st.pop();
        }
        
        // Removing leading zeroes
        while(ans.back() == '0'){
            ans.pop_back();
        }
        
        // Reverse to get the smallest number
        reverse(ans.begin(), ans.end());

        // In some cases, ans will be empty such as:
        // Ex: num = "9", k=1;  num = "45213" k = 5
        return ans.empty()  ? "0" : ans;
    }
};
```