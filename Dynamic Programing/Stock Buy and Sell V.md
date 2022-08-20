## Best Time to Buy and Sell Stock V
You are given an array prices where prices[i] is the price of a given stock on the ith day, and an integer fee representing a transaction fee.

Find the maximum profit you can achieve. You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
#### Example
```bash

Input: prices = [1,3,2,8,4,9], fee = 2
Output: 8
Explanation: The maximum profit can be achieved by:
- Buying at prices[0] = 1
- Selling at prices[3] = 8
- Buying at prices[4] = 4
- Selling at prices[5] = 9
The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.
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
                    # at the time of sell (buy-sell completed) fee will reduce
                    
                    profit= max(prices[ind]+ dp[ind+1][1] - fee,0 + dp[ind+1][0])
                dp[ind][buy]= profit
          
        return dp[0][1]
        
```

### Complexity

```bash
Time Complexity = O(n)
Space Complexity = O(n) 

```

[Best Time to Buy and Sell Stock V]([https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/))
