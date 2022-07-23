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
Time Complexity : O(3^n)
Space Complexity : O(n)  --> Stack space
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
    def maximumPath(self, N, Matrix):
        
        dp = [[-1 for _ in range(N)]for __ in range(N)]
        
        return self.solve(N,Matrix,N-1,0,dp)
    
    def solve(self,n,mat,i,j,dp):
        
        if i==0:return mat[0][j]
        
        if j<0 or j>=n:
            return 0
        
        if dp[i][j] != -1:
            dp[i][j] = mat[i][j]
            
        up = mat[i][j] + self.solve(n,mat,i-1,j,dp)
        left_digonal = mat[i][j] + self.solve(n,mat,i-1,j-1,dp)
        right_digonal = mat[i][j] + self.solve(n,mat,i-1,j+1,dp)
        
        
        dp[i][j] = max(up,left_digonal,right_digonal)
        
        return dp[i][j]
        
```
### Complexity
 
```bash
Time Complexity: O(n*n)
Space Complexity: O(n*n) +O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
class Solution:
    def maximumPath(self, N, Matrix):
        
        dp = [[-1 for _ in range(N)]for __ in range(N)]
        
        return self.solve(N,Matrix,dp)
    
    def solve(self,n,mat,dp):
        
        for j in range(n):
            dp[0][j] = mat[0][j]
            
        for i in range(1,n):
            for j in range(n):
                
                up = mat[i][j] + dp[i-1][j];
            
                leftDiagonal= mat[i][j];
                if(j-1>=0):
                    leftDiagonal += dp[i-1][j-1];
                else:
                    leftDiagonal += -1e9;
            
                rightDiagonal = mat[i][j];
                if(j+1<n):
                    rightDiagonal += dp[i-1][j+1];
                else:
                    rightDiagonal += -1e9;
            
                dp[i][j] = max(up,leftDiagonal,rightDiagonal);
        
        
        ans = -99999
        for j in range(n):
            if ans < dp[n-1][j]:
                ans =dp[n-1][j]
                
        return ans
        
```
```bash
Time Complexity : O(n*n) + O(n)
Space Complexity : O(n*n)

## Geeksforgeeks
[Maximum Path Sum in Matrix](https://practice.geeksforgeeks.org/problems/path-in-matrix3805/1)
