## Minimum number of deletions and insertions
Given two strings str1 and str2. The task is to remove or insert the minimum number of characters from/in str1 so as to transform it into str2.
It could be possible that the same character needs to be removed/deleted from one point of str1 and inserted to some another point.
## Example
```bash
Input: str1 = "heap", str2 = "pea"
Output: 3
Explanation: 2 deletions and 1 insertion
p and h deleted from heap. Then, p is 
inserted at the beginning One thing to 
note, though p was required yet it was 
removed/deleted first from its position 
and then it is inserted to some other 
position. Thus, p contributes one to the 
deletion_count and one to the 
insertion_count.

```

## Solution 1 (Recursion)

```Python

class Solution:
	def minOperations(self, s1, s2):
        x=len(s1)
        y=len(s2)
        return self.lcs(x,y,s1,s2)

  
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
            
        sim1 = x - dp[x][y]
        sim2 = y - dp[x][y]
    
        return sim1+sim2
        
```
### Complexity
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```




## GeeksforGeeks
[Minimum number of deletions and insertions](https://practice.geeksforgeeks.org/problems/minimum-number-of-deletions-and-insertions0209/1)
