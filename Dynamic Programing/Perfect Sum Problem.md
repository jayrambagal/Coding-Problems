## Perfect Sum Problem

Given an array arr[] of non-negative integers and an integer sum, the task is to count all subsets of the given array with a sum equal to a given sum.

Note: Answer can be very large, so, output answer modulo 109+7
#### Example
```bash

Input: N = 6, arr[] = {2, 3, 5, 6, 8, 10}
       sum = 10
Output: 3
Explanation: {2, 3, 5}, {2, 8}, {10}



```
### Solution 

```python
class Solution:
	def perfectSum(self, arr, n, sum):
		
		return self.solve(arr,n,0,sum,0)
		
	def solve(self,arr,n,i,sum,count):
        
	    
	    if (i == n):
            if (sum == 0):
                count += 1
            return count
 
        count = self.solve(arr, n, i + 1, sum - arr[i],count)
        count = self.solve(arr, n, i + 1, sum, count)
        return count
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution 

```python
class Solution:
    
	def perfectSum(self, arr, n, sum):
	    
		dp = [[0 for _ in range(sum+1)]for __ in range(n+1)]
		
		for j in range(sum+1):
		    dp[0][j] = 0
		for i in range(n+1):
		    dp[i][0] = 1
		    
		for i in range(1,n+1):
		    for j in range(1,sum+1):
		    
		        if arr[i-1]<=j:
		            
		            dp[i][j] = dp[i-1][j-arr[i-1]] + dp[i-1][j]
		            
		        else:
		            dp[i][j] = dp[i-1][j]
		            
		return dp[n][sum]


        
```
### Complexity
```bash

```


