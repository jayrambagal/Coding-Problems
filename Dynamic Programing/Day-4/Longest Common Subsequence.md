## Longest Common Subsequence
Given two sequences, find the length of longest subsequence present in both of them. Both the strings are of uppercase.
## Example
```bash
Input:
A = 6, B = 6
str1 = ABCDGH
str2 = AEDFHR
Output: 3
Explanation: LCS for input Sequences
“ABCDGH” and “AEDFHR” is “ADH” of
length 3.

```

## Solution 1 (Recursion)

```Python

class Solution:

    def lcs(self,x,y,s1,s2):
        
        if x==0 or y==0:
            return 0
            
        if (s1[x-1]==s2[y-1]):
            return self.lcs(x-1,y-1,s1,s2) + 1
            
        return max((self.lcs(x,y-1,s1,s2)) ,(self.lcs(x-1,y,s1,s2)) )
        
```
### Complexity
 
```bash
Time Complexity : O(2^n * 2^m )
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:

    def lcs(self,x,y,s1,s2):
        
        dp = [[-1] * (y + 1) for _ in range(x + 1)]
        
        return self.solve(x,y,s1,s2,dp)
        
    def solve(self,x,y,s1,s2,dp):
        
        if x==0 or y==0:
            return 0
        if dp[x][y] != -1:
            return dp[x][y]

            
        if (s1[x-1]==s2[y-1]):
            dp[x][y] = self.solve(x-1,y-1,s1,s2,dp) + 1
        else:
            dp[x][y] =  max((self.solve(x,y-1,s1,s2,dp)) ,(self.solve(x-1,y,s1,s2,dp)) )  
            
        return dp[x][y] 
```
### Complexity
 
```bash
Time Complexity: O(n*m)
Space Complexity: O(n*m) + O(n+m) -->Oxilary stack space
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
class Solution:
    
    def lcs(self,x,y,s1,s2):
        
        dp = [[-1] * (y + 1) for _ in range(x + 1)]
        
        for i in range(x+1):
            for j in range(y+1):
                
        
                if i==0 or j==0:
                    dp[i][j] = 0
                
                elif (s1[i-1]==s2[j-1]):
                    dp[i][j] = dp[i-1][j-1] + 1
                else:
                    dp[i][j] = max(dp[i][j-1],dp[i-1][j] )  
            
        return dp[x][y]  

```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```

## GeeksforGeeks
[Longest Common Subsequence](https://practice.geeksforgeeks.org/problems/longest-common-subsequence-1587115620/1)
