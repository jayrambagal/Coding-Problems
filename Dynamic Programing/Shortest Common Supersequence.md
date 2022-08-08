## Shortest Common Supersequence
Given two strings X and Y of lengths m and n respectively, find the length of the smallest string which has both, X and Y as its sub-sequences.
Note: X and Y can have both uppercase and lowercase letters.
## Example
```bash
Input:
X = abcd, Y = xycd
Output: 6
Explanation: Shortest Common Supersequence
would be abxycd which is of length 6 and
has both the strings as its subsequences.

```
### Approach

ans = (n+m) - lcs

## Solution 1 

```Python

class Solution:
    
    #Function to find length of shortest common supersequence of two strings.
    def shortestCommonSupersequence(self, X, Y, m, n):
        
        
    
        L = [[0 for i in range(n+1)] for j in range(m+1)]
 
        for i in range(m+1):
            for j in range(n+1):
                if i == 0 or j == 0:
                    L[i][j] = 0
                elif X[i-1] == Y[j-1]:
                    L[i][j] = L[i-1][j-1] + 1
                else:
                    L[i][j] = max(L[i-1][j], L[i][j-1])
 
        ans = (n+m) - L[m][n]
        return ans
         
        
```
### Complexity
 
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```



## GeeksforGeeks
[Shortest Common Supersequence](https://practice.geeksforgeeks.org/problems/shortest-common-supersequence0322/1)
