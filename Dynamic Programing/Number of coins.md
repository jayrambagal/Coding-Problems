## Number of coins
Given a value V and array coins[] of size M, the task is to make the change for V cents,
given that you have an infinite supply of each of coins{coins1, coins2, ..., coinsm} valued coins.
Find the minimum number of coins to make the change. If not possible to make change then return -1.

 
## Example 1


```bash
Input: V = 30, M = 3, coins[] = {25, 10, 5}
Output: 2
Explanation: Use one 25 cent coin
and one 5 cent coin


Input: V = 11, M = 4,coins[] = {9, 6, 5, 1} 
Output: 2 
Explanation: Use one 6 cent coin
and one 5 cent coin
```
## Solution 1 (recursion) 
```Python
class Solution:
	def minCoins(self, coins, M, V):
	    
	    return self.solve(coins,M,V)
	        
	def solve(self,coins,m,v):
	    
	    if v==0:
	        return 0
	    
	    res = 99999999999
	    
	    for i in range(m):
	        
	        if coins[i] <= v:
	            
	            ans = self.solve(coins,m,v-coins[i])
	            
	            res = min(res,ans+1)
	        
	    return res
```
## Recursion
```python
def solve(self, n, coins, amt):
    if amt == 0:
        return 0
    
    if n == 0 and amt != 0:
        return 99999
    
    if coins[n-1] > amt:
        return self.solve(n-1, coins, amt)
    
    return min(self.solve(n-1, coins, amt), self.solve(n, coins, amt-coins[n-1]) + 1)
```
	    
    

```bash
Time Complexity : O(2^n)
Space Complexity : O(1)
```
## geeksforgeeks
[Number of coins](https://practice.geeksforgeeks.org/problems/number-of-coins1824/1?page=2&difficulty[]=1&category[]=Dynamic%20Programming&sortBy=submissions)
