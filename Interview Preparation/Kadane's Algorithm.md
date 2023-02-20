## Kadane's Algorithm
Given an array Arr[] of N integers. Find the contiguous sub-array(containing at least one number) 
which has the maximum sum and return its sum.

## Example 
```bash
Input:
N = 5
Arr[] = {1,2,3,-2,5}
Output:
9
Explanation:
Max subarray sum is 9
of elements (1, 2, 3, -2, 5) which 
is a contiguous subarray.

```

## Solution 

```python
class Solution:
    
    def maxSubArraySum(self,arr,N):
        
        max_ans = -1e9
        ans = 0
        
        for i in arr:
            ans+=i
            max_ans = max(ans,max_ans)
            
            if ans<0:
                ans = 0
        return max_ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[Kadane's Algorithm](https://practice.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1)
