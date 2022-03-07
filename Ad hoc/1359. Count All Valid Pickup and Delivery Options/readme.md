# [1359. Count All Valid Pickup and Delivery Options](https://leetcode.com/problems/count-all-valid-pickup-and-delivery-options/)

**Author:** Yaswanth Haridasu <br> 
**Profile:** https://leetcode.com/_Riddler_/ <br>
**Solved on:** 6th February 2022

## Problem Statement:
Given n orders, each order consist in pickup and delivery services. 

Count all valid pickup/delivery possible sequences such that delivery(i) is always after of pickup(i). 

Since the answer may be too large, return it modulo 10^9 + 7.

**Example 1:** <br>
**Input:** n = 2<br>
**Output:** 6 <br>
All possible orders are (P1,P2,D1,D2), (P1,P2,D2,D1), (P1,D1,P2,D2), (P2,P1,D1,D2), (P2,P1,D2,D1) and (P2,D2,P1,D1)

**Example 2:** <br>
**Input:** n = 3<br>
**Output:** 90 <br>

**Constraint:** 1 <= n<= 500

## Approach:
Check this solution https://leetcode.com/problems/count-all-valid-pickup-and-delivery-options/discuss/1824664/0ms-oror-C%2B%2B-oror-Detailed-Explaination-with-Diagrams

## Solution: 
```cpp
// Ad Hoc
// Time: O(n)
// Space: O(1)

class Solution {
public:
    int countOrders(int n) {
	    int MOD = 1e9+7;
        long ans = 1;
		// Here i is no.of orders we've 
        for(int i=2; i<=n; i++){
            int remainingCells = 2*i-1;
			// i = no.of pickup services we've to fill the first cell
			// remainingPlaces = no.of cells available to fill the corresponding delivery service
            ans = ((i*remainingCells)%MOD * ans%MOD)%MOD;
        }
        return ans;
    }
};
```