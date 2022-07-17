## Painting the Fence
Given a fence with n posts and k colors, find out the number of ways of painting the fence so that not more than two consecutive fences have the same colors. Since the answer can be large return it modulo 10^9 + 7.
## Example 1


```bash
Input:
N=3,  K=2 
Output: 6

```

## Solution 1 (Recursion)

```Python

class Solution:
    def countWays(self,n,k):
        return self.solve(n,k)
        
    
    def solve(self,n,k):
        
        if n==1:return k
        
        if n==2:
            return self.add(k,self.mul(k,k-1))
            
        ans = self.add(self.mul(self.solve(n-2,k),k-1) , self.mul(self.solve(n-1,k),k-1))
        
        return ans
        
        
        
    def add(self,a,b):
        mod = pow(10,9) + 7
        return ((a % mod) + (b % mod)) % mod
    
    def mul(self,a,b):
        mod = pow(10,9) + 7;
        return ((a % mod) * (b % mod)) % mod
        
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
    def countWays(self,n,k):
        dp =[-1]*(n+1)
        return self.solve(n,k,dp)
        
    
    def solve(self,n,k,dp):
        
        if n==1:return k
        
        if n==2:
            return self.add(k,self.mul(k,k-1))
        
        if dp[n] != -1:
            return dp[n]
            
        dp[n] = self.add(self.mul(self.solve(n-2,k,dp),k-1) , self.mul(self.solve(n-1,k,dp),k-1))
        
        return dp[n]
        
        
        
    def add(self,a,b):
        mod = pow(10,9) + 7
        return ((a % mod) + (b % mod)) % mod
    
    def mul(self,a,b):
        mod = pow(10,9) + 7;
        return ((a % mod) * (b % mod)) % mod
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

class Solution:
    def countWays(self,n,k):
        return self.solve(n,k)
        
    def solve(self,n,k):
        
        dp = [-1]*(n+2)
        dp[1] = k
        dp[2] =self.add(k,self.mul(k,k-1))
        
        for i in range(3,n+1):
            dp[i] = self.add(self.mul(dp[i-2],k-1) , self.mul(dp[i-1],k-1))
            
        return dp[n]
        
    def add(self,a,b):
        mod = pow(10,9) + 7
        return ((a % mod) + (b % mod)) % mod
    
    def mul(self,a,b):
        mod = pow(10,9) + 7;
        return ((a % mod) * (b % mod)) % mod
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

class Solution:
    def countWays(self,n,k):
        return self.solve(n,k)
        
    def solve(self,n,k):
        if n==1:return k
        prev2 = k
        prev1 =self.add(k,self.mul(k,k-1))
        
        for i in range(3,n+1):
            ans = self.add(self.mul(prev2,k-1) , self.mul(prev1,k-1))
            prev2 = prev1
            prev1 = ans
            
        return prev1
        
    def add(self,a,b):
        mod = pow(10,9) + 7
        return ((a % mod) + (b % mod)) % mod
    
    def mul(self,a,b):
        mod = pow(10,9) + 7;
        return ((a % mod) * (b % mod)) % mod
```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Painting the Fence](https://practice.geeksforgeeks.org/problems/painting-the-fence3727/1)
