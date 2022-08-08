## Longest Common Palindromic Subsequence
Given a string s, find the longest palindromic subsequence's length in s.

A subsequence is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.
## Example
```bash
Input: s = "bbbab"
Output: 4
Explanation: One possible longest palindromic subsequence is "bbbb".

```

## Solution 2 (Dynamic Programing)

```Python
class Solution:
    def longestPalindromeSubseq(self, S1: str) -> int:
        
        S2 = S1[::-1]
        x = len(S1)
        y = len(S2)
        
        return self.lcs(x,y,S1,S2)
        
    def lcs(self,x,y,s1,s2):
        
        dp = [[-1] * (y + 1) for _ in range(x + 1)]
        
        for i in range(x+1):
            for j in range(y+1):
                    
                if i==0 or j==0:
                    dp[i][j] = 0
                
                elif (s1[i-1]==s2[j-1]):
                    dp[i][j] = dp[i-1][j-1] + 1
                else:
                    dp[i][j] = max(dp[i][j-1],dp[i-1][j] )  
            
        return dp[x][y]  
```
### Complexity
 
```bash
Time Complexity: O(n*m)
Space Complexity: O(n*m)
```

## LeetCode
[Longest Common Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/)
