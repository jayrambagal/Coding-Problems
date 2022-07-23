## Maximum Path Sum in Matrix
Given a NxN matrix of positive integers. There are only three possible moves from a cell Matrix[r][c].

Matrix [r+1] [c]
Matrix [r+1] [c-1]
Matrix [r+1] [c+1]
Starting from any column in row 0 return the largest sum of any of the paths up to row N-1.

 ## Example
```bashInput: N = 2
Matrix = {{348, 391},
          {618, 193}}
Output: 1009
Explaination: The best path is 391 -> 618. 
It gives the sum = 1009.

Input: N = 2
Matrix = {{2, 2},
          {2, 2}}
Output: 4
Explaination: No matter which path is 
chosen, the output is 4.

```

## Solution 1 (Recursion)

```Python

class Solution:
    def maximumPath(self, N, Matrix):
        
        return self.solve(N,Matrix,N-1,0)
    
    def solve(self,n,mat,i,j):
        
        if i==0:return mat[0][j]
        
        if j<0 or j>=n:
            return 0
            
        up = mat[i][j] + self.solve(n,mat,i-1,j)
        left_digonal = mat[i][j] + self.solve(n,mat,i-1,j-1)
        right_digonal = mat[i][j] + self.solve(n,mat,i-1,j+1)
        
        
        return max(up,left_digonal,right_digonal)
    
```
### Complexity
 
```bash
Time Complexity : O(2^n*m)
Space Complexity : O(m+n)  --> Stack space
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
def minimumPathSum(triangle, n):
    dp = [[-1 for _ in range(n)]for __ in range(n)]
    return solve(triangle,n,0,0,dp)

def solve(triangle,n,i,j,dp):
    
    if i == n-1:
        return triangle[n-1][j]
    if dp[i][j] != -1:
        return dp[i][j]
        
    down = triangle[i][j] + solve(triangle,n,i+1,j,dp)
    diagonal = triangle[i][j] + solve(triangle,n,i+1,j+1,dp)
    
    dp[i][j] = min(down,diagonal)
    
    return dp[i][j]
        
```
### Complexity
 
```bash
Time Complexity: O(m*n)
Space Complexity: O(m*n) + O(m+n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
def minimumPathSum(triangle, n):
    
    return solve(triangle,n)

def solve(triangle,n):
    
    dp = [[-1 for _ in range(n)]for __ in range(n)]
    
    for j in range(n):
        dp[n-1][j] = triangle[n-1][j]
        
    for i in range(n-2,-1,-1):
        for j in range(i,-1,-1):
            
            down = triangle[i][j] + dp[i+1][j]
            diagonal = triangle[i][j] + dp[i+1][j+1]
            
            dp[i][j] = min(down,diagonal)    
    
    return dp[0][0]

```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)

## LeetCode
[Maximum Path Sum in Matrix](https://practice.geeksforgeeks.org/problems/path-in-matrix3805/1)
