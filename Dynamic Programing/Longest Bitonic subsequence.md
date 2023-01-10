## Longest Bitonic subsequence
Given an array of positive integers. Find the maximum length of Bitonic subsequence. 
A subsequence of array is called Bitonic if it is first strictly increasing, then strictly decreasing.
 
#### Example
```bash

Input: nums = [1, 2, 5, 3, 2]
Output: 5
Explanation: The sequence {1, 2, 5} is
increasing and the sequence {3, 2} is 
decreasing so merging both we will get 
length 5.
```
### Solution 

```python
class Solution:
	def LongestBitonicSequence(self, arr):
	    
	    lis,lds = [0]*n , [0]*n
	    lis[0] = 1
	    for i in range(1,n):
	        count = 1
	        for j in range(i):
	            if arr[i]>arr[j]:
	                count = max(count,1+lis[j])
	            
	        lis[i] = count
	    
	    
	    lds[n-1]=1
	    for k in range(n-2,-1,-1):
	        count = 1
	        for l in range(k+1,n):
	            if arr[k]>arr[l]:
	                count = max(count,1+lds[l])
	 
	        lds[k] = count
	    
        ans = 0            
    	for i in range(n):
    	    ans = max(ans,(lds[i]+lis[i])-1)
    	return ans
       
        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+ O(n)
```


[Longest Bitonic subsequence](https://practice.geeksforgeeks.org/problems/longest-bitonic-subsequence0824/1)
