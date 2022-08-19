## Longest Sub-Array with Sum K
Given an array containing N integers and an integer K., Your task is to find the length of the longest Sub-Array with the sum of the elements equal to the given value K.


## Example 
```bash
Input :
A[] = {10, 5, 2, 7, 1, 9}
K = 15
Output : 4
Explanation:
The sub-array is {5, 2, 7, 1}.

```

```python
import sys
class Solution:
    def lenOfLongSubarr (self, arr, n, k) : 
        
        mydict = dict()
 
        sum = 0
        maxLen = 0
 
  
        for i in range(n):
 
            sum += arr[i]
 
            if (sum == k):
                maxLen = i + 1
 
            elif (sum - k) in mydict:
                maxLen = max(maxLen, i - mydict[sum - k])
 
        
            if sum not in mydict:
                mydict[sum] = i
 
        return maxLen
        
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)

```

## Solution 
```python
import sys
 
def lenOfLongSubarr(A, N, K):
 
    i, j, sum = 0, 0, 0
    maxLen = -sys.maxsize -1
   
    while (j < N):
        sum += A[j]
        if (sum < K):
            j += 1
        elif (sum == K):
            maxLen = max(maxLen, j - i + 1)
            j += 1
        elif (sum > K):
            while (sum > K):
                sum -= A[i]
                i += 1
            if (sum == K):
                  maxLen = max(maxLen, j - i + 1)
            j += 1
    return maxLen
        
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```

## Geeksforgeeks
[Longest Sub-Array with Sum K](https://practice.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)
