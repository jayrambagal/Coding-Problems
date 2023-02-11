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
```python
class Solution:
	def longSubarrWthSumDivByK (self,arr,  n, k) : 
	    um = {}
 
        mod_arr = [0 for i in range(n)]
        max_len = 0
        curr_sum = 0
     
        for i in range(n):
            curr_sum += arr[i]
     
            mod_arr[i] = ((curr_sum % k) + k) % k
     
            if (mod_arr[i] == 0):
     
                max_len = i + 1
     
            elif (mod_arr[i] not in um):
                um[mod_arr[i]] = i
     
            else:
                max_len = max(max_len, i - um[mod_arr[i]] ) 
                
        return max_len
```

## Geeksforgeeks
[Longest subarray with sum divisible by K](https://practice.geeksforgeeks.org/problems/longest-subarray-with-sum-divisible-by-k1259/1?page=1&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=prefix-sum&sortBy=submissions)
