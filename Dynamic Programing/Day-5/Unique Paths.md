## Unique Paths
There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.

 

## Example
```bash
Input: m = 3, n = 7
Output: 28
Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down

```

## Solution 1 (Recursion)

```Python

class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        return self.solve(m-1,n-1)
    
    def solve(self,i,j):
        
        if i<0 or j<0:
            return 0
        
        if i==0 and j==0:
            return 1
            
        up = self.solve(i-1,j,dp)
        left = self.solve(i,j-1,dp)
        
        return up+left
        
```
### Complexity
 
```bash
Time Complexity : O(2^n*m)
Space Complexity : O(m+n)  --> Stack space
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [[-1 for _ in range(n)] for __ in range(m)]
        return self.solve(m-1,n-1,dp)
    
    def solve(self,i,j,dp):
        
        if i<0 or j<0:
            return 0
        
        if i==0 and j==0:
            return 1
        
        if dp[i][j] != -1:
            return dp[i][j]
        else:
        
            up = self.solve(i-1,j,dp)
            left = self.solve(i,j-1,dp)
        
            dp[i][j] = up + left
        
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
[Ninjas training](https://www.codingninjas.com/codestudio/problems/ninja-s-training_3621003?source=youtube&campaign=striver_dp_videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_dp_videos&leftPanelTab=1)
