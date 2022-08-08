## Form a palindrome
Given a string, find the minimum number of characters to be inserted to convert it to palindrome.
For Example:
ab: Number of insertions required is 1. bab or aba
aa: Number of insertions required is 0. aa
abcd: Number of insertions required is 3. dcbabcd

## Example
```bash
Input: str = "abcd"
Output: 3
Explanation: Inserted character marked
with bold characters in dcbabcd

```
## Approach

n - Longest palindromic Subsequence

## Solution 2 (Dynamic Programing)

```Python
class Solution:
    def countMin(self, S1):
        
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
            
        return x - dp[x][y]  
```
### Complexity
 
```bash
Time Complexity: O(n*m)
Space Complexity: O(n*m)
```

## GFG
[Form a Palindrome](https://practice.geeksforgeeks.org/problems/form-a-palindrome1455/1)
