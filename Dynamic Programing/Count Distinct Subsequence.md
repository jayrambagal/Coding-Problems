##  Distinct Subsequences
Given two strings S and T of length n and m respectively. find count of distinct occurrences of T in S as a sub-sequence. 

## Example
```bash

Input:
S = "banana" , T = "ban"
Output: 3
Explanation: There are 3 sub-sequences:
[ban], [ba n], [b an].

```

## Solution 1 (Recursion)

```Python

class Solution:
    def sequenceCount(self,s, t):
        def countWays(i,j):
        
            if j<0:
                return 1
        
            if i<0:
                return 0
        
            if s[i]==t[j]:
                pick=countWays(i-1,j-1)
                notPick=countWays(i-1,j)
        
                return pick+notPick
    
            else:
                return countWays(i-1,j)
        
        m=len(s)
        n=len(t)
        if n>m:
            return 0
        return countWays(m-1,n-1)
        
```
### Complexity
 
```bash
Time Complexity : Exponential
Space Complexity : O(n+m)
```

## Solution 2  --> Memoiation
```Python
class Solution:
    def sequenceCount(self,s, t):
    
        def countWays(i,j,dp):
        
            if j<0:
                return 1
        
            if i<0:
                return 0
            
            if dp[i][j] != -1:
                return dp[i][j]
        
            if s[i]==t[j]:
                pick=countWays(i-1,j-1,dp)
                notPick=countWays(i-1,j,dp)
                dp[i][j] = pick+notPick
                return dp[i][j] % 1000000007
    
            else:
                dp[i][j] = countWays(i-1,j,dp)
                return dp[i][j] % 1000000007
        
        m=len(s)
        n=len(t)
        dp = [[-1 for _ in range(n+1)]for __ in range(m+1)]
        if n>m:
            return 0
        
        return countWays(m-1,n-1,dp)

```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m) + O(n+m)
```
## Solution 3 --> Tabulation
```python

class Solution:
    def sequenceCount(self,s, t):
        n=len(s)
        m=len(t)
        dp=[[0 for _ in range(m+1)] for _ in range(n+1)]
        
        for i in range(n+1):
            dp[i][0] = 1
                    
        for i in range(1,n+1):
            for j in range(1,m+1):
                if s[i-1]==t[j-1]:
                    dp[i][j]=dp[i-1][j-1]+dp[i-1][j]
                else:
                    dp[i][j]=dp[i-1][j]
                    
        return dp[n][m] %1000000007
        
```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```

## GeeksforGeeks
[Distinct Subsequences](https://practice.geeksforgeeks.org/problems/distinct-occurrences/1)
