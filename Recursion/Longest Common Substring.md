## Longest Common Substring
Given two strings. The task is to find the length of the longest common substring.## Example
```bash

Input: S1 = "ABCDGH", S2 = "ACDGHR", n = 6, m = 6
Output: 4
Explanation: The longest common substring
is "CDGH" which has length 4.

```

## Solution 1 (Recursion)

```Python

class Solution:
    def longestCommonSubstr(self, S1, S2, n, m):
        
        return self.solve(S1,S2,n,m,0)
        
    def solve(self,X,Y,i,j,count):
        
        if (i == 0 or j == 0):
            return count
 
        if (X[i - 1] == Y[j - 1]):
            count = self.solve(X,Y,i - 1, j - 1, count + 1) 
 
        count = max(count, max(self.solve(X,Y,i, j - 1, 0),
                           self.solve(X,Y,i - 1, j, 0)))
 
        return count
        
```
### Complexity
 
```bash
Time Complexity : O(3^n*m )
Space Complexity : O(n)
```


## GeeksforGeeks
[Longest Common Substring](https://practice.geeksforgeeks.org/problems/longest-common-substring1452/1?page=1&difficulty[]=1&category[]=Dynamic%20Programming&category[]=Recursion&sortBy=submissions)
