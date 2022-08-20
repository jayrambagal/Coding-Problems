## Best Time to Buy and Sell Stock III
You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete at most two transactions.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
#### Example
```bash

Input: prices = [3,3,5,0,0,3,1,4]
Output: 6
Explanation: Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.



```
## Approach

### Solution (Recursion)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        return self.solve(0,1,prices,2)  # intialy limit will be 2
    
    def solve(self,index,buy,prices,limit):
        
        if index==len(prices):
            return 0
        if limit == 0:
            return 0
        
        profit = 0
        
        if buy==1:
            profit = max( (-prices[index]+ self.solve(index+1,0,prices,limit)) ,(0+self.solve(index+1,1,prices,limit)) )
            
            
        else:
        
            # when buy and sell Complete limit will Decrement by 1
            
            profit = max( (prices[index]+ self.solve(index+1,1,prices,limit-1)) ,(0+self.solve(index+1,0,prices,limit)) )
            
        return profit
       
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution (Memoiation)--> 3D DP

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        dp = [[[-1 for i in range(3)]for j in range(2)]for k in range(n+1)]
        return self.solve(0,1,prices,2,dp)
    
    def solve(self,index,buy,prices,limit,dp):
        
        if index==len(prices):
            return 0
        if limit == 0:
            return 0
        
        if dp[index][buy][limit] != -1:
            return dp[index][buy][limit]
        
        profit = 0
        
        if buy==1:
            profit = max( (-prices[index]+ self.solve(index+1,0,prices,limit,dp)) ,(0+self.solve(index+1,1,prices,limit,dp)) )
            
            
        else:
            profit = max( (prices[index]+ self.solve(index+1,1,prices,limit-1,dp)) ,(0+self.solve(index+1,0,prices,limit,dp)) )
            
        dp[index][buy][limit]  = profit
        
        return dp[index][buy][limit]
        
```
### Complexity
```bash
Time Complexity = O(n*2*3)
Space Complexity = O(n*2*3)+O(n) 
```
## Solution (Tabulation)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        
        return self.solve(prices)
    
    def solve(self,prices):
        n = len(prices)
        
        dp = [[[0 for i in range(3)]for j in range(2)]for k in range(n+1)]
        
        for ind in range(n-1,-1,-1):
            for buy in range(2):
                for limit in range(1,3):
                    profit = 0
                    if(buy):
                        profit= max(-prices[ind] +dp[ind+1][0][limit], 0 +  dp[ind+1][1][limit])
                    
                    else:
                        profit= max(prices[ind]+dp[ind+1][1][limit-1],0 + dp[ind+1][0][limit])
                        
                    dp[ind][buy][limit]= profit
          
        return dp[0][1][2]
        
```

### Complexity

```bash
Time Complexity = O(n*2*3)
Space Complexity = O(n*2*3) 

```

[Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
