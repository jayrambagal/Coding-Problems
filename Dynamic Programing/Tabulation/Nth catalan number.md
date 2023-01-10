## Nth catalan number
Given a number N. The task is to find the Nth catalan number.
The first few Catalan numbers for N = 0, 1, 2, 3, … are 1, 1, 2, 5, 14, 42, 132, 429, 1430, 4862, …
Note: Positions start from 0 as shown above.

#### Example
```bash

Input:
N = 4
Output: 14
```

### Solution 

```python
class Solution:
    #Function to find the nth catalan number.
    def findCatalan(self,n):
        
        dp = [0]*(n+1)
        dp[0]=1
        dp[1]=1
        
        for i in range(2,n+1):
            for j in range(0,i):
                dp[i]+= dp[j]*dp[i-j-1]
        return dp[n]
        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+O(n) 
```


[Nth catalan number](https://practice.geeksforgeeks.org/problems/nth-catalan-number0817/1)
