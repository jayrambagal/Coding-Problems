## Subarrays with equal 1s and 0s
Given an array containing 0s and 1s. Find the number of subarrays having equal numbers of 0s and 1s.

## Example 
```bash
Input:
n = 7
A[] = {1,0,0,1,0,1,1}
Output: 8
Explanation: The index range for the 8 
sub-arrays are: (0, 1), (2, 3), (0, 3), (3, 4), 
(4, 5) ,(2, 5), (0, 5), (1, 6)

Input:
n = 5
A[] = {1,1,1,1,0}
Output: 1
Explanation: The index range for the 
subarray is (3,4).

```

## Solution
```python
class Solution:
 
    def countSubarrWithEqualZeroAndOne(self,arr, n):
        
        summ = 0
        count = 0
        
        mapp = dict()
        
        for i in range(n):
            if arr[i]==0:
                arr[i] = -1
                
            summ+=arr[i]
            
            if summ == 0:
                count+=1
                
            if summ in mapp.keys():
                count+=mapp[summ]
                
            mapp[summ] = mapp.get(summ,0)+1
            
        return count
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[LaSubarrays with equal 1s and 0s](https://practice.geeksforgeeks.org/problems/count-subarrays-with-equal-number-of-1s-and-0s-1587115620/1?page=1&difficulty[]=1&status[]=unsolved&curated[]=2&sortBy=submissions)
