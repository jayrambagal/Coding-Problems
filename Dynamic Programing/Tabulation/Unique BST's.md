## Unique BST's

Given an integer. Find how many structurally unique binary search trees are there that stores the values from 1 to that integer (inclusive). 

#### Example
```bash
Input:
N = 3
Output: 5
Explanation: for N = 3, there are 5
possible BSTs
  1           3     3       2     1
    \        /     /      /  \     \
     3      2     1      1    3     2
    /      /       \                 \
   2      1         2                 3
```

### Solution 

```python
class Solution:
    #Function to return the total number of possible unique BST.
    def numTrees(self,n):
        mod = 1000000007
        dp = [0]*(n+1)
        dp[0]=1
        dp[1]=1

        for i in range(2,n+1):
            for j in range(i):
                dp[i]+= dp[j]*dp[i-j-1]

        return dp[n]%mod
        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+O(n) 
```


[Unique BST's](https://practice.geeksforgeeks.org/problems/unique-bsts-1587115621/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)

