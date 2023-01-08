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
for checking subset sum is present or not and also print the all paths equal to sum.
![IMG_20230108_231724 1](https://user-images.githubusercontent.com/94613732/211211132-ff96c82a-fe7e-4323-815f-715188443c08.jpg)
![IMG_20230108_231738 1](https://user-images.githubusercontent.com/94613732/211211154-26cd8a40-da19-4b17-9c62-8b5faf858727.jpg)



```python
from collections import deque
class Solution:
	def perfectSum(self, arr, n, tar):
	    
	    dp = [[False for i in range(tar+1)] for j in range(n+1)]
	    for i in range(n+1):
	        dp[i][0]=True
	        
	    for i in range(1,n+1):
	        for j in range(tar+1):
	            
	            if (dp[i-1][j]):
	                dp[i][j] = True
	                
	            elif (j>=arr[i-1]):
	                if (dp[i-1][j-arr[i-1]]):
	                    dp[i][j] = True
	  
	    # BFS
	    
	    q = deque()
	    q.append((n,tar))
	    count = 0
	    while q:
	        i,j = q.popleft()
	        
	        if i==0 and j==0:
	            count+=1
	        else:
    	        exc = dp[i-1][j]
    	        
    	        if exc:
    	            q.append((i-1,j))
    	        
    	        if j>=arr[i-1]:
    	            inc = dp[i-1][j-arr[i-1]]
    	            if inc:
    	                q.append((i-1,j-arr[i-1]))
    	                
	    return count


        
```
### Complexity
```bash

```


