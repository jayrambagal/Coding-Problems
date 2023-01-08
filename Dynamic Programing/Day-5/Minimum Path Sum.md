## Minimum path sum --> only move to right and down
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

 ## Example
```bash

Input: grid = [[1,3,1],[1,5,1],[4,2,1]]
Output: 7
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.

```

## Solution 1 (Recursion)

```Python

class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        
        m =len(grid)
        n =len(grid[0])
        
        return self.solve(m-1,n-1,grid)
    
    def solve(self,i,j,grid):
        
        if i<0 or j<0:return 1e9
        
        if i==0 and j==0:return grid[0][0]
        
        up = grid[i][j] + self.solve(i-1,j,grid)
        left = grid[i][j] + self.solve(i,j-1,grid)
        
        return min(up,left)
```
### Complexity
 
```bash
Time Complexity : O(2^n*m)
Space Complexity : O(m+n)  --> Stack space
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m =len(grid)
        n =len(grid[0])
        dp = [[-1 for _ in range(n+1)]for __ in range(m+1)]
        
        return self.solve(m-1,n-1,grid,dp)
    
    def solve(self,i,j,grid,dp):
        
        if i<0 or j<0:return 1e9
        
        if i==0 and j==0:return grid[0][0]
        
        if dp[i][j] != -1: return dp[i][j]
        
        up = grid[i][j] + self.solve(i-1,j,grid,dp)
        left = grid[i][j] + self.solve(i,j-1,grid,dp)
        
        dp[i][j] = min(up,left)
        
        return dp[i][j]
        
```
### Complexity
 
```bash
Time Complexity: O(m*n)
Space Complexity: O(m*n) + O(m+n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if i > 0 and j > 0:
                    grid[i][j] = min(grid[i][j] + grid[i-1][j], grid[i][j] + grid[i][j-1])
                elif i > 0:
                    grid[i][j] += grid[i-1][j]
                elif j > 0:
                    grid[i][j] += grid[i][j-1]
        
        return grid[-1][-1]

```
```bash
Time Complexity : O(n*m)
Space Complexity : 
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python


```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/submissions/)
