## Maximum Sub Array
Find out the maximum sub-array of non negative numbers from an array.

The sub-array should be contiguous i.e., a sub-array created by choosing the second and fourth element and skipping the third element is invalid.

Maximum sub-array is defined in terms of the sum of the elements in the sub-array. Sub-array A is greater than sub-array B if sum(A) > sum(B).

## Example 
```bash
input
Input:
N = 3
A[] = {1, 2, 3}
Output: 1 2 3
Explanation: In the given array every
element is non-negative.

Input:
N = 3
A = [1, 4, -3, 9, 5, -6]
Output: 9 5

```
## Solution

```python

class Solution:

	def findSubarray(self,arr, n):
	    ans = [-1]
	    max_sum = 0
	    summ = 0
	    start = 0
	    end = 0
	    curr = 0
	    
	    for i in range(n):
	        if arr[i]<0:
	            summ = 0
	            curr = i+1
	        else:
	            summ+=arr[i]
	            
	        if max_sum <= summ:
	            max_sum = summ
	            start = curr
	            end = i
	            
	    if max_sum == 0:
	        return ans
	    else:
	        return arr[start:end+1]
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(1)

```
## Geeksforgeeks
[Maximum Sub Array](https://practice.geeksforgeeks.org/problems/maximum-sub-array5443/1?page=3&difficulty[]=1&category[]=Arrays&sortBy=submissions)

