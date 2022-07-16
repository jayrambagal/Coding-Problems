## Fibonacci Number
You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor
## Example 1


```bash
Input: cost = [10,15,20]
Output: 15
Explanation: You will start at index 1.
- Pay 15 and climb two steps to reach the top.
The total cost is 15.


Input: cost = [1,100,1,1,1,100,1,1,100,1]
Output: 6
Explanation: You will start at index 0.
- Pay 1 and climb two steps to reach index 2.
- Pay 1 and climb two steps to reach index 4.
- Pay 1 and climb two steps to reach index 6.
- Pay 1 and climb one step to reach index 7.
- Pay 1 and climb two steps to reach index 9.
- Pay 1 and climb one step to reach the top.
The total cost is 6.

```

## Solution 1 (Recursion)

```Python

class Solution:
    
    def solve(self,cost,n):
        
        if n ==0:return cost[0]
        if n==1: return cost[1]
        
        ans = cost[n] + min(self.solve(cost,n-1),self.solve(cost,n-2))
        
        return ans
        
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        n = len(cost)
        ans = min(self.solve(cost,n-1),self.solve(cost,n-2))
        return ans
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python

class Solution:
    
    def solve(self,cost,n,dp):
        
        if n ==0:return cost[0]
        if n==1: return cost[1]
        
        if dp[n]!= -1:
            return dp[n]
        
        dp[n] = cost[n] + min(self.solve(cost,n-1,dp),self.solve(cost,n-2,dp))
        
        return dp[n]
        
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        n = len(cost)
        dp = [-1]*(n+1)
        ans = min(self.solve(cost,n-1,dp),self.solve(cost,n-2,dp))
        return ans

```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> space optimization
```Python
class Solution:
    
    def solve(self,cost,n):
        
        prev1 = cost[1]
        prev2 = cost[0]
        
        for i in range(2,n):
            curr = cost[i]+ min(prev1,prev2) 
            prev2 = prev1
            prev1 = curr
            
            
        return min(prev1,prev2)
        
        
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        n = len(cost)
        return self.solve(cost,n)
```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## LeetCode
[Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)
