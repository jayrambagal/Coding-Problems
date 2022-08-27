## Longest subarray with sum divisible by K
Given an array containing N integers and a positive integer K, find the 

length of the longest sub array with sum of the elements divisible by the given value K.

## Example 
```bash
Input:
A[] = {2, 7, 6, 1, 4, 5}
K = 3
Output: 4
Explanation:The subarray is {7, 6, 1, 4}
with sum 18, which is divisible by 3.

```


## Solution

```python

class Solution:
	def longSubarrWthSumDivByK (self,arr,  n, K) : 
	    
	    count = 0
	    summ = 0
	    ans = 0
	    
	    for i in range(n):
	        summ = arr[i]
	        count = 1
	        if summ%K==0:
	            ans = max(ans,count)
	        for j in range(i+1,n):
	            summ+=arr[j]
	            count+=1
	            
	            if summ%K==0:
	                ans = max(ans,count)
	                
	    return ans
```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity : O(1)

```

## Geeksforgeeks
[Longest subarray with sum divisible by K](https://practice.geeksforgeeks.org/problems/longest-subarray-with-sum-divisible-by-k1259/1?page=1&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=prefix-sum&sortBy=submissions)
