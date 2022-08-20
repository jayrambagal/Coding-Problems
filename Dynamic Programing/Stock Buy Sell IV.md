## Best Time to Buy and Sell Stock IV
You are given an integer array prices where prices[i] is the price of a given stock on the ith day, and an integer k.

Find the maximum profit you can achieve. You may complete at most k transactions.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
#### Example
```bash
Input: k = 2, prices = [2,4,1]
Output: 2
Explanation: Buy on day 1 (price = 2) and sell on day 2 (price = 4), profit = 4-2 = 2.



```
## Approach

### Solution (Recursion)

```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        return self.solve(0,0,k,prices)
    
    def solve(self,index,oparation,k,prices):
        
        n=len(prices)
        
        if index==n:
            return 0
        if oparation == k*2:
            return 0
        
        if oparation%2==0:
            profit = max( (-prices[index]+ self.solve(index+1,oparation+1,k,prices)) ,(0+self.solve(index+1,oparation,k,prices)) )
            
        else:
            profit = max( (prices[index]+ self.solve(index+1,oparation+1,k,prices)) ,(0+self.solve(index+1,oparation,k,prices)) )
        
        return profit
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution (Memoiation)

```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        n=len(prices)
        dp = [[-1 for i in range(2*k+1)]for i in range(n+1)]
        return self.solve(0,0,k,prices,dp)
    
    def solve(self,index,oparation,k,prices,dp):
        
        n=len(prices)
        
        if index==n:
            return 0
        if oparation == k*2:
            return 0
        if dp[index][oparation]!= -1:
            return dp[index][oparation]
        
        if oparation%2==0:
            profit = max( (-prices[index]+ self.solve(index+1,oparation+1,k,prices,dp)) ,(0+self.solve(index+1,oparation,k,prices,dp)) )
            
        else:
            profit = max( (prices[index]+ self.solve(index+1,oparation+1,k,prices,dp)) ,(0+self.solve(index+1,oparation,k,prices,dp)) )
        
        dp[index][oparation] = profit
        
        return dp[index][oparation]
        
```
### Complexity
```bash
Time Complexity = O(n*2*k)
Space Complexity = O(n*2*k)+O(n) 
```
## Solution (Tabulation)

```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
       
        return self.solve(0,0,k,prices)
    
    def solve(self,index,oparation,k,prices):
        n=len(prices)
        dp = [[0 for i in range(2*k+1)]for i in range(n+1)]
        
        
        for index in range(n-1,-1,-1):
            for oparation in range(0,2*k):
                if oparation%2==0:
                    profit = max( (-prices[index]+ dp[index+1][oparation+1]),(dp[index+1][oparation]) )
            
                else:
                    profit = max( (prices[index]+ dp[index+1][oparation+1]),(dp[index+1][oparation]) )
        
                dp[index][oparation] = profit
        
        return dp[0][0]
        
```

### Complexity

```bash
Time Complexity = O(n*2*k)
Space Complexity = O(n*2*k) 

```

[Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
