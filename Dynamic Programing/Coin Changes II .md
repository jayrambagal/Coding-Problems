## Coin Changes

You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the number of combinations that make up that amount. If that amount of money cannot be made up by any combination of the coins, return 0.

You may assume that you have an infinite number of each kind of coin.

The answer is guaranteed to fit into a signed 32-bit integer.



 
## Example 1


```bash
Input: amount = 5, coins = [1,2,5]
Output: 4
Explanation: there are four ways to make up the amount:
5=5
5=2+2+1
5=2+1+1+1
5=1+1+1+1+1
```
## Solution 1 (recursion) 
```Python

class Solution:

    def change(self, amt: int, coins: List[int]) -> int:
    
        def solve(amt, i):
	
            if i == 0:
                return int(not amt % coins[0]) # if amt is not divisible by coins[0] then coins[0]th element can not made a target(amt).
		
            dont = solve(amt, i-1)
	    
            take = 0
	    
            if amt - coins[i] >= 0:
                take = solve(amt-coins[i], i)
		
            return take+dont
	    
        return solve(amt, len(coins)-1)
        
```
#### Complexity
```bash
Time Complexity : Exponentioal
Space Complexity : greater than O(n)
```
## Solution (Memoiation)
```python
class Solution:
    def change(self, amt: int, coins: List[int]) -> int:
        dp = [[-1 for i in range(amt+1)]for i in range(len(coins)+1)]
        def solve(amt, i):
            if i == 0:
                return int(not amt % coins[0])
            
            if dp[i][amt]!= -1:
                return dp[i][amt]
            
            dont = solve(amt, i-1)
            take = 0
            if amt - coins[i] >= 0:
                take = solve(amt-coins[i], i)
            dp[i][amt] = take+dont
            return dp[i][amt]
        return solve(amt, len(coins)-1)
```

```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```

## Solution (Tabulation)
```python

class Solution:
    def change(self, amt: int, coins: List[int]) -> int:
        
        n = len(coins)
        dp = [[0]*(amt+1) for _ in range(n)]
        
        for i in range(amt+1):
            dp[0][i] = int(not i % coins[0])
            
        for i in range(1, n):
            for j in range(amt+1):
                
                dont = dp[i-1][j]
                take = 0
                if j - coins[i] >= 0:
                    take = dp[i][j-coins[i]]
                    
                dp[i][j] = take+dont
                
        return dp[-1][amt]

```
	    
    

```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## Leetcode
[coin changes II](https://leetcode.com/problems/coin-change-2/submissions/)
