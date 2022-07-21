## Unique Paths
You are given an m x n integer array grid. There is a robot initially located at the top-left corner (i.e., grid[0][0]).
The robot tries to move to the bottom-right corner (i.e., grid[m-1][n-1]). The robot can only move either down or right 
at any point in time.An obstacle and space are marked as 1 or 0 respectively in grid. A path that the robot takes cannot 
include any square that is an obstacle.Return the number of possible unique paths that the robot can take to reach the 
bottom-right corner.The testcases are generated so that the answer will be less than or equal to 2 * 109.

 ## Example
```bash

Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
Output: 2
Explanation: There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -> Right -> Down -> Down
2. Down -> Down -> Right -> Right

```

## Solution 1 (Recursion)

```Python

class Solution:
    
    def uniquePathsWithObstacles(self, grid: List[List[int]]) -> int:
        n = len(grid)
        m = len(grid[0])
		
        
        return self.finduniquePaths(n-1,m-1,grid)
    
    def finduniquePaths(self,n,m,grid):
        
        if grid[n][m] == 1:
            return 0
		
        if n == 0 and m == 0:
            return 1
        
        if n < 0 or m < 0:
            return 0
        
        
        left = self.finduniquePaths(n,m-1,grid)
        up = self.finduniquePaths(n-1,m,grid)
        
        return left+up
```
### Complexity
 
```bash
Time Complexity : O(2^n*m)
Space Complexity : O(m+n)  --> Stack space
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
    
    def uniquePathsWithObstacles(self, grid: List[List[int]]) -> int:
        n = len(grid)
        m = len(grid[0])
		
		
        dp = [[-1 for _ in range(m)] for _ in range(n)]

        return self.finduniquePaths(n-1,m-1,grid,dp)
    
    def finduniquePaths(self,n,m,grid,dp):
	
        if grid[n][m] == 1:
            return 0
		
        if n == 0 and m == 0:
            return 1
		 
        if n < 0 or m < 0:
            return 0
        
		
        if dp[n][m] != -1:
            return dp[n][m]
        
        left = self.finduniquePaths(n,m-1,grid,dp)
        up = self.finduniquePaths(n-1,m,grid,dp)
        
		
        dp[n][m] = left + up
        return dp[n][m]
        
```
### Complexity
 
```bash
Time Complexity: O(m*n)
Space Complexity: O(m*n) + O(m+n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        
        return self.solve(m,n)
    
    def solve(self,m,n):
        dp = [[-1 for _ in range(n)] for __ in range(m)]
        
        for i in range(m):
            for j in range(n):
                
                if i==0 and j==0:
                    dp[i][j] =1
                else:
                    up = 0
                    left = 0
                    
                    if i>0:
                        up = dp[i-1][j]
                    if j>0:
                        left = dp[i][j-1]
                    
                    dp[i][j] = up + left
                
        return dp[m-1][n-1]

```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python


```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)
