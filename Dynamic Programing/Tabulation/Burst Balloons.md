## Burst Balloons
You are given N balloons, indexed from 0 to n - 1. Each balloon is painted with a number on it represented by an array arr. 

You are asked to burst all the balloons. If you burst the ith balloon, you will get arr[ i - 1 ] * arr[ i ] * arr[ i + 1] coins. 

If i - 1, or i + 1 goes out of the bounds of the array, consider it as if there is a balloon with a 1 painted on it.

Return the maximum coins you can collect by bursting the balloons wisely.

#### Example
```bash
Input:
N = 4
arr[ ] = {3, 1, 5, 8}
Output: 167
Explanation: 
arr[ ] = {3, 1, 5, 8}  - - > {3, 5, 8} - - > {3, 8} - - > { 8} - -> { }
coins = 3 *1 *5,      +      3*5*8     +   1*3*8   +  1*8*1   = 167
```


### Solution 

```python
class Solution:
    def maxCoins(self, n : int, arr : List[int]) -> int:
        
        dp = [[0 for i in range(n)]for j in range(n)]
        
        for g in range(n):
            i = 0
            j = g
            while j<n and i<n:
                maxx = -1e9
                for k in range(i,j+1):
                    
                    left = 0
                    if i!=k: 
                        left = dp[i][k-1] 
                    
                    right = 0
                    if j!=k: 
                        right = dp[k+1][j]
                    
                    val = arr[k]
                    
                    if i!=0:
                        val*=arr[i-1]
                    
                    if j!=n-1:
                        val*=arr[j+1]
                    
                    total = left+right+val
                    maxx = max(maxx,total)
                    
                dp[i][j] = maxx
                i+=1
                j+=1

        return dp[0][n-1]
        
```
### Complexity
```bash
Time Complexity = 
Space Complexity =  
```


[Burst Balloons](https://practice.geeksforgeeks.org/problems/burst-balloons/1)
