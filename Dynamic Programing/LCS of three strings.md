## LCS of three strings
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

## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:

    def LCSof3(self,A,B,C,n1,n2,n3):
        
        dp = [[[-1 for i in range(n3+1)]for j in range(n2+1)]for k in range(n1+1)]
        return self.solve(A,B,C,n1,n2,n3,dp)
        
    def solve(self,A,B,C,n,m,l,dp):
        
        if n==0 or m==0 or l==0:
            return 0
        if dp[n][m][l] != -1:
            return dp[n][m][l]
        
        if A[n-1] == B[m-1] == C[l-1]:
            dp[n][m][l] = self.solve(A,B,C,n-1,m-1,l-1,dp) + 1
            
        else:
            dp[n][m][l] = max(self.solve(A,B,C,n-1,m,l,dp) , 
                              self.solve(A,B,C,n,m-1,l,dp) , 
                              self.solve(A,B,C,n,m,l-1,dp))
                              
        return dp[n][m][l]
```
### Complexity
 
```bash
Time Complexity: O(n*m*l)
Space Complexity: O(n*m*l) + O(n+m+l) 
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
class Solution:

    def LCSof3(self,A,B,C,n1,n2,n3):
        
        dp = [[[0 for i in range(n3+1)]for j in range(n2+1)]for k in range(n1+1)]
        
        for i in range(1,n1+1):
            for j in range(1,n2+1):
                for k in range(1,n3+1):

                    if A[i-1]==B[j-1]==C[k-1]:
                        dp[i][j][k] = dp[i-1][j-1][k-1] +1
                        
                    else:
                        dp[i][j][k] = max(dp[i-1][j][k],dp[i][j-1][k],dp[i][j][k-1])
                        
        return dp[n1][n2][n3]  

```
```bash
Time Complexity : O(n*m*l)
Space Complexity : O(n*m*l)
```

## GeeksforGeeks
[LCS of three strings](https://practice.geeksforgeeks.org/problems/lcs-of-three-strings0028/1)
