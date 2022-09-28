## Count Smaller elements
 Given an array Arr of size N containing positive integers. 
 
 Count number of smaller elements on right side of each array element.

## Example 
```bash
Input:
N = 7
Arr[] = {12, 1, 2, 3, 0, 11, 4}
Output: 6 1 1 1 0 1 0
Explanation: There are 6 elements right
after 12. There are 1 element right after
1. And so on.

```

## Solution 

```python
from bisect import bisect_left
class Solution:

	def constructLowerArray(self,nums, n):
	    array = sorted(nums)

		result = []

		for num in nums:

			return_value = bisect_left(array, num)

			del array[return_value] 

			if  return_value == -1:
				result.append(0)

			else:
				result.append(return_value)

		return result
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```

 

## Geeksforgeeks
[Count Smaller elements](https://practice.geeksforgeeks.org/problems/count-smaller-elements2214/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Binary%20Search&sortBy=submissions)
