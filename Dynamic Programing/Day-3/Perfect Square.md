## Get Minimum Squares

Given a number N. Find the minimum number of squares of any number that sums to N. For Example: If N = 100 ,
N can be expressed as (10*10) and also as (5*5 + 5*5 + 5*5 + 5*5) but the output will be 1 as minimum number of square is 1 , i.e (10*10).
## Example 1


```bash
Input: N = 100
Output: 1
Explanation: 10 * 10 = 100

Input: N = 6
Output: 3
Explanation = 1 * 1 + 1 * 1 + 2 * 2 = 6



```

## Solution 1 (Recursion)

```Python
class Solution:
	def MinSquares(self, n):
	    
	    return self.solve(n)
	    
	def solve(self,n):
  
	    if n <=3:return n
        
	    if n==0: return 0
	    
	   
	    ans = n
	    for i in range(1,n+1):
	        temp = i*i
	        if temp > n:
                break
	        else:
	            ans = min(ans,1+ self.solve(n-temp))
	        
	    return ans
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
	def MinSquares(self, n):
	    dp=[-1]*(n+1)
	    return self.solve(n,dp)
	    
	def solve(self,n,dp):
	    
	    if n==0: return 0
	    
	    if dp[n] != -1:
	        return dp[n]
	    ans = n
	    for i in range(1,n+1):
	        temp = i*i
	        if temp > n:
                break
	        else:
	            ans = min(ans,1+ self.solve(n-temp,dp))
	            
	        dp[n] = ans
	        
	    return dp[n]
```
### Complexity
 

```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```python 
 from typing import List

def findWays(num: List[int], tar: int) -> int:

    n = len(num)
    dp = [0 for _ in range(tar + 1)]
    
    dp[0] = 1
    for i in range(1, tar+1):   # n time complexity
        for j in range(n):      # m 

            if i - num[j] >= 0:
                dp[i] += dp[i - num[j]]

    return dp[tar]
    
```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python
#Space optimization  Not Possible

```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Combination Sum IV](https://www.codingninjas.com/codestudio/problems/number-of-ways_3755252?leftPanelTab=1&utm_source=youtube&utm_medium=affiliate&utm_campaign=Lovebabbar)
