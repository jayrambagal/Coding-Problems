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


```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)

```

## Geeksforgeeks
[Maximum Index](https://practice.geeksforgeeks.org/problems/maximum-index3307/1?page=1&difficulty[]=1&company[]=Google&category[]=Arrays&sortBy=submissions)

