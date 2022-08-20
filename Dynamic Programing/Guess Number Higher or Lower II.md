## Guess Number Higher or Lower II

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
Explanation: The winning strategy is as follows:
- The range is [1,10]. Guess 7.
    - If this is my number, your total is $0. Otherwise, you pay $7.
    - If my number is higher, the range is [8,10]. Guess 9.
        - If this is my number, your total is $7. Otherwise, you pay $9.
        - If my number is higher, it must be 10. Guess 10. Your total is $7 + $9 = $16.
        - If my number is lower, it must be 8. Guess 8. Your total is $7 + $9 = $16.
    - If my number is lower, the range is [1,6]. Guess 3.
        - If this is my number, your total is $7. Otherwise, you pay $3.
        - If my number is higher, the range is [4,6]. Guess 5.
            - If this is my number, your total is $7 + $3 = $10. Otherwise, you pay $5.
            - If my number is higher, it must be 6. Guess 6. Your total is $7 + $3 + $5 = $15.
            - If my number is lower, it must be 4. Guess 4. Your total is $7 + $3 + $5 = $15.
        - If my number is lower, the range is [1,2]. Guess 1.
            - If this is my number, your total is $7 + $3 = $10. Otherwise, you pay $1.
            - If my number is higher, it must be 2. Guess 2. Your total is $7 + $3 + $1 = $11.
The worst case in all these scenarios is that you pay $16. Hence, you only need $16 to guarantee a win.



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
class Solution:
    def change(self, amt: int, coins: List[int]) -> int:
        dp = [[-1 for i in range(amt+1)]for i in range(len(coins)+1)]
        def solve(amt, i):
            if i == 0:
                return int(not amt % coins[0])
            
            if dp[i][amt]!= -1:
                return dp[i][amt]
            
            dont = solve(amt, i-1)
            take = 0
            if amt - coins[i] >= 0:
                take = solve(amt-coins[i], i)
            dp[i][amt] = take+dont
            return dp[i][amt]
        return solve(amt, len(coins)-1)
```

```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```

## Solution (Tabulation)
```python

class Solution:
    def change(self, amt: int, coins: List[int]) -> int:
        
        n = len(coins)
        dp = [[0]*(amt+1) for _ in range(n)]
        
        for i in range(amt+1):
            dp[0][i] = int(not i % coins[0])
            
        for i in range(1, n):
            for j in range(amt+1):
                
                dont = dp[i-1][j]
                take = 0
                if j - coins[i] >= 0:
                    take = dp[i][j-coins[i]]
                    
                dp[i][j] = take+dont
                
        return dp[-1][amt]

```
	    
    

```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## Leetcode
[coin changes II](https://leetcode.com/problems/coin-change-2/submissions/)
