## Maximize Number of 1's
Given a binary array arr of size N and an integer M. Find the maximum number of consecutive 1's produced by flipping at most M 0's.

## Example 
```bash
Input:
N = 11
arr[] = {1, 0, 0, 1, 1, 0, 1, 0, 1, 1, 1}
M = 2
Output:
8
Explanation:
Maximum subarray is of size 8
which can be made subarray of all 1 after
flipping two zeros to 1.

```

## Solution
```python
def findZeroes(arr, n, m) :
    
    i = 0
    start = 0
    ans = 0
    
    while i < n:
        
        if arr[i] == 0:
            m-=1
        
        if m>=0:
            ans = max(ans,i-start+1)
            
        elif m<0:
            while m<0:
                if arr[start]==0:
                    m+=1
                start+=1
        if m>=0:
            ans = max(ans,i-start+1)
            
        i+=1
    return ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

## Geeksforgeeks
[Maximize Number of 1's](https://practice.geeksforgeeks.org/problems/maximize-number-of-1s0905/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Recursion&category[]=Backtracking&sortBy=submissions)
