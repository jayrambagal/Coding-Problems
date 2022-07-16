## Disarrangement of balls
You are given N balls numbered from 1 to N and there are N baskets numbered from 1 to N in front of you, the ith basket is meant for the ith ball. Calculate the number of ways in which no ball goes into its respective basket.
## Example 1


```bash
Input: N = 2
Output: 1

Input: 3
Output: 2
Explanation: The (number-basket) pairs are 
[(1-3),(2-1),(3-2)] and [(1-2),(2-3),(3-2)].
```

## Solution 1 (Recursion)

```Python

class Solution:
    def disarrange(self, n):
        
        if n==1:return 0
            
        if n==2:return 1
        
        ans = (n-1)*(self.disarrange(n-1) + self.disarrange(n-2))
        
        return ans
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
from sys import stdin, setrecursionlimit
import sys
setrecursionlimit(10**6)

class Solution:
    def solve(self, n,dp):
        
        if n==1:return 0
            
        if n==2:return 1
        
        if dp[n] != -1: return dp[n]
        
        dp[n] = ((n-1)*(self.solve((n-1),dp) + self.solve((n-2),dp)))%1000000007
        
        return dp[n]
        
    def disarrange(self, n):
        dp = [-1]*(n+1)
        return self.solve(n,dp)
```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
from sys import stdin, setrecursionlimit
import sys
setrecursionlimit(10**6)
MOD = 1000000007



class Solution:
    
    def disarrange(self, n):
        return self.solve(n)
            
    def solve(self, n):
        
        dp = [0 for x in range(n+1)]
        
        dp[1] = 0
        dp[2] = 1
        
        for i in range(3,n+1):
            dp[i] = (((i - 1) * (dp[i - 1]  + dp[i - 2] ) )) % MOD
            
        return dp[n]
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python

from sys import stdin, setrecursionlimit
import sys
setrecursionlimit(10**6)
MOD = 1000000007



class Solution:
    
    def disarrange(self, n):
        return self.solve(n)
            
    def solve(self, n):
        prev2 = 0
        prev1 = 1
        
        for i in range(3,n+1): 
             
            summ = prev1 + prev2
            ans = ((i - 1) * summ ) % MOD
            
            prev2 = prev1
            prev1 = ans
            
        return prev1
```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Disarrangement of balls](https://practice.geeksforgeeks.org/problems/dearrangement-of-balls0918/1)
