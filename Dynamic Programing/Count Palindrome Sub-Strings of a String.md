## Count Palindrome Sub-Strings of a String
Given a string, the task is to count all palindromic sub-strings present 

in it. Length of palindrome sub-string must be greater than or equal to 2. 
## Example
```bash
Input
N = 5
str = "abaab"
Output
3
Explanation:
All palindrome substring are : "aba" , "aa" , "baab"

```

## Solution (Dynamic Programing)

```Python
class Solution:

    def CountPS(self, S, N):
        n = len(S)
        dp = [[False for i in range(n)]for j in range(n)]
        
        count = 0
        
        for g in range(n):
            i = 0
            for j in range(g,len(dp)):
                
                if g==0:
                    dp[i][j] = True
                elif g==1:
                    if S[i]==S[j]:
                        dp[i][j] = True
                    else:
                        dp[i][j] = False
                        
                else:
                    if S[i]==S[j] and dp[i+1][j-1] == True:
                        dp[i][j] = True
                    else:
                        dp[i][j] = False
                        
                if dp[i][j]:
                    count+=1
                    
                i+=1
                
        return count - n 
```
### Complexity
 
```bash
Time Complexity: O(n*n)
Space Complexity: O(n*n)
```

## LeetCode
[Count Palindrome Sub-Strings of a String](https://practice.geeksforgeeks.org/problems/count-palindrome-sub-strings-of-a-string0652/1?page=3&difficulty[]=1&status[]=unsolved&company[]=Amazon&category[]=Arrays&category[]=Strings&category[]=Hash&category[]=Sorting&category[]=Matrix&category[]=Linked%20List&category[]=Searching&category[]=Stack&category[]=Recursion&category[]=Binary%20Search%20Tree&category[]=Binary%20Search&sortBy=submissions)
