## Form a palindrome
Given a string, find the minimum number of characters to be inserted to convert it to palindrome.
## Example
```bash
Input: str = "abcd"
Output: 3
Explanation: Inserted character marked
with bold characters in dcbabcd

Input: str = "aa"
Output: 0
Explanation:"aa" is already a palindrome.

```


## Solution  (Dynamic Programing) --> Tabulation
```Python
class Solution:
    def countMin(self, Str):
        n = len(Str)
        Str2 = Str[::-1]
        ans = n - self.lcs(n,n,Str,Str2)
        
        return ans
        
    def lcs(self,x,y,s1,s2):      # find longest common Subsequence in tabulation method 
                                  # we can solve this by Memoiation or space optimization method
        
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
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```

## GeeksforGeeks
[Form a palindrome](https://practice.geeksforgeeks.org/problems/form-a-palindrome1455/1)


