## Triangle
Given a triangle array, return the minimum path sum from top to bottom.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index i on the current row, you may move to either index i or index i + 1 on the next row.
 ## Example
```bash

Input: triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]
Output: 11
Explanation: The triangle looks like:
   2
  3 4
 6 5 7
4 1 8 3
The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11 (underlined above).

```

## Solution 1 (Recursion)

```Python

def minimumPathSum(triangle, n):
   
    return solve(triangle,n,0,0)

def solve(triangle,n,i,j):
    
    if i == n-1:
        return triangle[n-1][j]
    
    down = triangle[i][j] + solve(triangle,n,i+1,j)
    diagonal = triangle[i][j] + solve(triangle,n,i+1,j+1)
    
    return min(down,diagonal)
    
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
[Unique Paths II](https://leetcode.com/problems/triangle/)
