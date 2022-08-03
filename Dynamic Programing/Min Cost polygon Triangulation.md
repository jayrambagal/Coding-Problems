## Minimum Score Triangulation of Polygon
You have a convex n-sided polygon where each vertex has an integer value. You are given an integer array values where values[i] is the value of the ith vertex (i.e., clockwise order).

You will triangulate the polygon into n - 2 triangles. For each triangle, the value of that triangle is the product of the values of its vertices, and the total score of the triangulation is the sum of these values over all n - 2 triangles in the triangulation.

Return the smallest possible total score that you can achieve with some triangulation of the polygon.

```bash

Input: values = [1,2,3]
Output: 6
Explanation: The polygon is already triangulated, and the score of the only triangle is 6.

```

## Solution 1 (Recursion)

```Python

class Solution:
    def minScoreTriangulation(self, values: List[int]) -> int:
        
        n = len(values)
        return self.solve(values ,0,n-1,dp)
    
    def solve(self,val,i,j):
        
        if (i+1 == j):
            return 0
            
        ans = 999999999
        for k in range(i+1,j):
            
            ans = min(ans,val[i]*val[j]*val[k] + self.solve(val,i,k)+self.solve(val,k,j))
            
        return ans
      
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```

## Solution 2  --> Memoiation
```Python
class Solution:
    def minScoreTriangulation(self, values: List[int]) -> int:
        
        n = len(values)
        
        dp = [[-1 for _ in range(n)]for __ in range(n)]
        
        return self.solve(values ,0,n-1,dp)
    
    def solve(self,val,i,j,dp):
        
        if (i+1 == j):
            return 0
        
        if dp[i][j] != -1:
            return dp[i][j]
        
        ans = 999999999
        for k in range(i+1,j):
            
            ans = min(ans,val[i]*val[j]*val[k] + self.solve(val,i,k,dp)+self.solve(val,k,j,dp))
            
            dp[i][j] = ans
            
        return dp[i][j]

```
```bash
Time Complexity : O(n)
Space Complexity : O(n) + O(n)
```

## Solution 2  --> Tabulation
```Python
class Solution:
    def minScoreTriangulation(self, val: List[int]) -> int:
        
        n = len(val)
        
        dp = [[0 for _ in range(n+1)]for __ in range(n+1)]
        
        for i in range(n-1,-1,-1):
            for j in range(i+2,n):
                
                ans = 9999999999
                
                for k in range(i+1,j):
            
                    ans = min(ans,val[i]*val[j]*val[k] + dp[i][k] +dp[k][j])
                              
                    dp[i][j] = ans
            
        return dp[i][n-1]

```
```bash
Time Complexity : O(n)
Space Complexity : O(n) + O(n)
```
## Leetcode
[Minimum Score Triangulation of Polygon](https://leetcode.com/problems/minimum-score-triangulation-of-polygon/)
