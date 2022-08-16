## Maximum Index
Given an array Arr[] of N positive integers. The task is to find the maximum of j - i subjected to the constraint of Arr[i] <= Arr[j].

## Example 
```bash
N = 9
Arr[] = {34, 8, 10, 3, 2, 80, 30, 33, 1}
Output: 6

```
## Solution (brutforce)

```python

class Solution:

	def maxIndexDiff(self,arr,n):
	    ans = 0
	    for i in range(n):
	        for j in range(i+1,n):
	            
	            if arr[i]<=arr[j]:
	                ans = max(ans,j-i)
		return ans
```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity : O(1)

```
## Solution (optimized)

```python
class Solution:

	def maxIndexDiff(self,arr,n):
	   
	    
	    main = [0]*n
	    main[0] = arr[0]
	    
	    for i in range(1,n):
	        main[i] = min(main[i-1],arr[i])
	        
	    i = n-1
	    j = n-1
	    ans = 0
	    
	    while i>=0 and j>=0:
	        
	        if arr[j]>=main[i]:
	            ans = max(ans,j-i)
	            i-=1
	            
	        else:
	            j-=1
	            
	    return ans

```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)

```

## Geeksforgeeks
[Maximum Index](https://practice.geeksforgeeks.org/problems/maximum-index3307/1?page=1&difficulty[]=1&company[]=Google&category[]=Arrays&sortBy=submissions)

