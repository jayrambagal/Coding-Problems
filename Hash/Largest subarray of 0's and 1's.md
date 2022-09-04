## Largest subarray of 0's and 1's
Given an array of 0s and 1s. Find the length of the largest subarray with equal number of 0s and 1s.

## Example 
```bash
Input:
N = 4
A[] = {0,1,0,1}
Output: 4
Explanation: The array from index [0...3]
contains equal number of 0's and 1's.
Thus maximum length of subarray having
equal number of 0's and 1's is 4.

```

## Solution
```python
class Solution:
    def maxLen(self,arr, N):
        
        freq = {0:-1}
        ans = 0
        ind = 0
        summ = 0
        
        for i in range(N):
            if arr[i]==0:
                summ =summ -1
            else:
                summ+= 1
                
            if summ in freq:
                #finding the index position of first summ occurred in map 
                ind = freq.get(summ)  
                ans = max(ans,abs(ind-i))
            else:
                freq[summ] = i
                
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Largest subarray of 0's and 1's](https://practice.geeksforgeeks.org/problems/largest-subarray-of-0s-and-1s/1?page=1&status[]=unsolved&category[]=sliding-window&sortBy=submissions)
