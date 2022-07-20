## Largest square formed in a matrix
Given a binary matrix mat of size n * m, find out the maximum size square sub-matrix with all 1s.## Example 1


```bash
Input: n = 2, m = 2
mat = {{1, 1}, 
       {1, 1}}
Output: 2
Explaination: The maximum size of the square
sub-matrix is 2. The matrix itself is the 
maximum sized sub-matrix in this case.
```

## Solution 1 (Recursion)

```Python

class Solution:
    def maxSquare(self, n, m, matrix):
        
        def recurse(i, j):
            
            if i >= n or j >= m or matrix[i][j] == 0:
                return 0
                
            else:
                res = min(recurse(i+1, j), recurse(i, j+1), recurse(i+1, j+1)) + 1
            
            return res
        
        ans = 0
        
        for i in range(n):
            for j in range(m):
                ans = max(ans, recurse(i, j))
            
        return ans
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
    def maxSquare(self, n, m, matrix):
        dp = [[-1 for _ in range(m+1)] for _ in range(n+1)]
        
        def recurse(i, j):
            if dp[i][j] != -1:
                return dp[i][j]
            
            if i >= n or j >= m or matrix[i][j] == 0:
                dp[i][j] = 0
            else:
                dp[i][j] = min(recurse(i+1, j), recurse(i, j+1), recurse(i+1, j+1)) + 1
            
            return dp[i][j]
        
        ans = 0
        
        for i in range(n):
            for j in range(m):
                ans = max(ans, recurse(i, j))
            
        return ans 
```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python

```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python


```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Largest square formed in a matrix](https://practice.geeksforgeeks.org/problems/largest-square-formed-in-a-matrix0806/1)
