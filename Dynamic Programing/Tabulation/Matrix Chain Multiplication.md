## Matrix Chain Multiplication
Given a sequence of matrices, find the most efficient way to multiply these matrices together. The efficient way is the one that 

involves the least number of multiplications. The dimensions of the matrices are given in an array arr[] of size N (such that N = number of matrices + 1) 

where the ith matrix has the dimensions (arr[i-1] x arr[i]).

#### Example
```bash
Input: N = 5
arr = {40, 20, 30, 10, 30}
Output: 26000
Explaination: There are 4 matrices of dimension 
40x20, 20x30, 30x10, 10x30. Say the matrices are 
named as A, B, C, D. Out of all possible combinations,
the most efficient way is (A*(B*C))*D. 
The number of operations are -
20*30*10 + 40*20*10 + 40*10*30 = 26000.
```

### Solution 

```python
class Solution:
    def matrixMultiplication(self, n, arr):
        
        dp = [[0 for i in range(n-1)]for j in range(n-1)]
        
        for g in range(n-1):
            i= 0 
            j = g
            while i<n-1 and j<n-1:
                if g==0:
                    dp[i][j] = 0
                elif g==1:
                    dp[i][j] =  arr[i]*arr[j]*arr[j+1]
                else:
                    minn = 1e9
                    for k in range(i,j):
                        
                        lc = dp[i][k]
                        rc = dp[k+1][j]
                        
                        mc = dp[i][k] + rc + arr[i]*arr[k+1]*arr[j+1]
                        ans = mc
                        minn = min(minn,ans)
                        
                    dp[i][j] = minn
                i+=1
                j+=1

        return dp[0][-1]
        
```
### Complexity
```bash
Time Complexity = 
Space Complexity =  
```


[Matrix Chain Multiplication](https://practice.geeksforgeeks.org/problems/matrix-chain-multiplication0303/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
