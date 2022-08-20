## Guess Number Higher or Lower II
[Guess Number Higher or Lower II](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)

We are playing the Guessing Game. The game will work as follows:

I pick a number between 1 and n.
You guess a number.
If you guess the right number, you win the game.

If you guess the wrong number, then I will tell you whether the number I picked is higher or lower, and you will continue guessing.

Every time you guess a wrong number x, you will pay x dollars. If you run out of money, you lose the game.

Given a particular n, return the minimum amount of money you need to guarantee a win regardless of what number I pick.



 
## Example 1


```bash
Input: n = 10
Output: 16

Input: n = 1
Output: 0
Explanation: There is only one possible number, so you can guess 1 and not have to pay anything.

```
## Solution 1 (recursion) 
```Python

import sys
class Solution:
    def getMoneyAmount(self, n: int) -> int:
        
        return self.solve(1,n)
    
    def solve(self,start,end):
        if start>=end:
            return 0
        
        ans = sys.maxsize
        for i in range(start,end):
            
            ans = min(ans, i+max(self.solve(start,i-1),self.solve(i+1,end)))
            
        return ans
        
```
#### Complexity
```bash
Time Complexity : Exponentioal
Space Complexity : greater than O(n)
```
## Solution (Memoiation)
```python
import sys
class Solution:
    def getMoneyAmount(self, n: int) -> int:
        dp = [[-1 for i in range(n+1)]for i in range(n+1)]
        return self.solve(1,n,dp)
    
    def solve(self,start,end,dp):
        if start>=end:
            return 0
        if dp[start][end]!=-1:
            return dp[start][end]
        
        ans = sys.maxsize
        for i in range(start,end):
            
            ans = min(ans, i+max(self.solve(start,i-1,dp),self.solve(i+1,end,dp)))
            dp[start][end] = ans
        return dp[start][end]
```

```bash
Time Complexity : O(n^2)
Space Complexity : O(n^2) + O(n)
```

## Solution (Tabulation)
```python
import sys
class Solution:
    def getMoneyAmount(self, n: int) -> int:
        dp = [[0 for i in range(n+2)]for i in range(n+2)]
        
        for start in range(n,0,-1):
            for end in range(start,n+1):
                
                if start==end:
                    continue
                else:
                    
                    ans = sys.maxsize
                    for i in range(start,end):
            
                        ans = min(ans,(i+max( dp[start][i-1] , dp[i+1][end] )))
                                  
                        dp[start][end] = ans
        return dp[1][n]
```
	    
```bash
Time Complexity : O(n^2)
Space Complexity : O(n^2)
```
## Leetcode
[Guess Number Higher or Lower II](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)
