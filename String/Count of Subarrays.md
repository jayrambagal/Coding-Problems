## Count of Subarrays
Given an array of N positive integers  Arr1, Arr2 ............ Arrn. The value of each contiguous 

subarray of given array is the maximum element present in that subarray. The task is to return the 

number of subarrays having value strictly greater than K.

## Example 
```bash
N = 3, K = 2
Arr[] = {3, 2, 1}
Output: 3
Explanation: The subarrays having value
strictly greater than K are: [3], [3, 2]
and [3, 2, 1]. Thus there are 3 such
subarrays.

Input:
N = 4, K = 1
Arr[] = {1, 2, 3, 4}
Output: 9
Explanation: There are 9 subarrays having
value strictly greater than K.
```


## Solution 

```python
class Solution:
	def countSubarray(self,arr, n, k):
	    
	    s = 0
        i = 0
        
        while (i < n):
         
            if (arr[i] > k):
                i = i + 1
            
            count = 0
            while (i < n and arr[i] <= k):
                i = i + 1
                count = count + 1
             
            s = s + ((count*(count + 1))//2)
         
      
        return (n*(n + 1)//2 - s)

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

## Geeksforgeeks
[Count of Subarrays](https://practice.geeksforgeeks.org/problems/count-of-subarrays5922/1)
