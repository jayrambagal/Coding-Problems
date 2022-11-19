## Largest Sum Subarray of Size at least K

Given an array and a number k, find the largest sum of the subarray containing at 

least k numbers. It may be assumed that the size of array is at-least k.

#### Example
```bash
Input : 
n = 4
arr[] = {-4, -2, 1, -3}
k = 2
Output : 
-1
Explanation :
The sub array is {-2, 1}

Input :
n = 6 
arr[] = {1, 1, 1, 1, 1, 1}
k = 2
Output : 
6
Explanation :
The sub array is {1, 1, 1, 1, 1, 1}

```
### Solution 

```python
import sys
def maxSumWithK( a, n, k):
    
    summ = 0
    for i in range(k):
        summ += a[i]
 
    last = 0
    j = 0
    ans = -sys.maxsize - 1
    ans = max(ans, summ)
    for i in range(k, n):
        summ += a[i]
        last = last + a[j]
        j += 1
        ans = max(ans, summ)
        if(last < 0):
            summ = summ-last
            ans = max(ans, summ)
            last = 0
    return ans
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(1) 
```


## Leetcode       
[Largest Sum Subarray of Size at least K](https://practice.geeksforgeeks.org/problems/largest-sum-subarray-of-size-at-least-k3121/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=sliding-window&sortBy=submissions)
