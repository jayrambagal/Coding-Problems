## Perfect Squares

Given an integer n, return the least number of perfect square numbers that sum to n.

A perfect square is an integer that is the square of an integer; in other words, 

it is the product of some integer with itself. For example, 1, 4, 9, and 16 are perfect squares while 3 and 11 are not.

#### Example
```bash
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```

### Solution 

```python
class Solution:
    def numSquares(self, n: int) -> int:
        
        dp=[0]*(n+1)
        dp[1] = 1
        for i in range(2,n+1):
            c = 1e9
            for j in range(1,i+1):
                if j*j<=i:
                    c = min(c,dp[i-j*j])
                else:
                    break
            dp[i] = c+1
        print(dp)
        return dp[n]

        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+O(n) 
```


[Perfect Squares](https://leetcode.com/problems/perfect-squares/description/)
