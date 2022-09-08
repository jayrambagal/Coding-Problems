## Longest subarray with sum divisible by K
```
Given an array containing N integers and a positive integer K, find the length 
of the longest sub array with sum of the elements divisible by the given value K.
```

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

	    max_sum = -99999999
	    
	    for i in range(n):
	        count = 0
	        summ = 0
	        for j in range(i,n):
	            summ+=arr[j]
	            if summ%K == 0:
	                count = (j-i)+1
	                
	        max_sum = max(max_sum,count)
	        
	    return max_sum
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```

## Geeksforgeeks
[Longest subarray with sum divisible by K](https://practice.geeksforgeeks.org/problems/longest-subarray-with-sum-divisible-by-k1259/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&sortBy=submissions)
