# [1675. Minimize Deviation in Array](https://leetcode.com/problems/minimize-deviation-in-array/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 20th February 2022

## Problem Statement:
You are given an array nums of n positive integers.

You can perform two types of operations on any element of the array **any number of times**:

- If the element is even, divide it by 2.
- If the element is odd, multiply it by 2.

The **deviation** of the array is the **maximum difference** between any two elements in the array.

Return the **minimum deviation** the array can have after performing some number of operations.

**Example:** <br>
**Input:** nums = [4,1,5,20,3] <br>
**Output:** 3

## Approach:
To get the minimum deviation, we try to maximize the smallest value and minimize the largest value

**Maximizing smallest value:** <br>
- If the smallest number is odd, then we can multiply it by 2 to maximize it.
- If the smallest number is even, then we cannot do anything to maximize it because dividing by 2 only minimizes it

**Minimizing largest value:** <br>
- If the largest value is odd, then we cannot do anything to minimize it. Hence, it'll be the final largest value.
- If the largest value is even, then we can divide it by 2 and minimize it.


## Solution: 
```cpp
// Priority Queue
// Time: O(n(logm)logn); m = max(nums)
// Space: O(n)
class Solution {
public:
    int minimumDeviation(vector<int>& nums) {
        // Storing all the elements in the heap
        priority_queue<int> heap;

        // Storing the smallest element
        int smallest = INT_MAX;
        
        for(int i=0; i<nums.size(); i++){
            int ele = nums[i];
            // If odd, it can be maximized
            if(ele&1){
                ele <<= 1;
            }
            heap.push(ele);
            // Updating the smallest value
            smallest = min(smallest, ele);
        }
        // Now, let's find the largest value from the heap and try to minimize it
        int ans = INT_MAX;
        // If the largest value is odd, then it is the smallest largest value
        while(!heap.empty() && heap.top()%2==0){
            int largest = heap.top();
            heap.pop();
            // Updating the min deviation
            ans = min(ans, largest-smallest);
            // Dividing it by 2 and pushing back to heap
            largest >>= 1;
            heap.push(largest);
            // Updating the smallest
            smallest = min(smallest, largest);
        }

        // As the heap top is odd, find the deviation
        ans = min(ans, heap.top()-smallest);
        return ans;
    }
};
```