## Best Time to Buy and Sell Stock II

You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock.

You can only hold at most one share of the stock at any time.

However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.
#### Example
```bash

Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.



```
### Solution (Recursion)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        return self.solve(0,1,prices)
    
    def solve(self,index,buy,prices):
        
        if index==len(prices):
            return 0
        
        profit = 0
        
        if buy==1:
            profit = max( (-prices[index]+ self.solve(index+1,0,prices)) ,(0+self.solve(index+1,1,prices)) )
            
            
        else:
            profit = max( (prices[index]+ self.solve(index+1,1,prices)) ,(0+self.solve(index+1,0,prices)) )
            
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

    class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        dp = [[-1 for i in range(2)]for i in range(n+1)]
        return self.solve(0,1,prices,dp)
        
    def solve(self,index,buy,prices,dp):
        
        if index==len(prices):
            return 0
        if dp[index][buy] != -1:
            return dp[index][buy]
        
        profit = 0
        
        if buy==1:
            profit = max( (-prices[index]+ self.solve(index+1,0,prices,dp)) ,(0+self.solve(index+1,1,prices,dp)) )
            
            
        else:
            profit = max( (prices[index]+ self.solve(index+1,1,prices,dp)) ,(0+self.solve(index+1,0,prices,dp)) )
            
        dp[index][buy] = profit
        
        return dp[index][buy]
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n)+O(n) 
```
## Solution (Tabulation)

```python
class Solution:
     def maxProfit(self, prices):
        n = len(prices)
        dp =  [[0 for i in range(2)] for i in range(n+1)]
        
        
        for ind in range(n-1,-1,-1):
            for buy in range(2):
                
                if(buy):
                    profit= max(-prices[ind] +dp[ind+1][0], 0 +  dp[ind+1][1])
                    
                else:
                    profit= max(prices[ind]+dp[ind+1][1],0 + dp[ind+1][0])
                dp[ind][buy]= profit
          
        return dp[0][1]
        
```

### Complexity

```bash
Time Complexity = O(n)
Space Complexity = O(n) 

```

[Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

