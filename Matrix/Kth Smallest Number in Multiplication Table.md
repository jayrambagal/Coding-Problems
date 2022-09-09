## Kth Smallest Number in Multiplication Table
Given three integers M, N and K. Consider a grid of M * N, where mat[i][j] = i * j (1 based index). 

The task is to return the Kth smallest element in the M * N multiplication table.

## Example 
```bash
Input:
M = 3, N = 3
K = 5
Output: 3
Explanation: 

The 5th smallest element is 3.


```
## Solution (Brut force)

```python

class Solution(object):
    def findKthNumber(self, m, n, k):
        
        arr = []
        i = 1
        while i<m+1:
            j=1
            while j <n+1:
                arr.append(i*j)
                j+=1
            i+=1
                
        arr.sort()       
        return arr[k-1]
```
## Complexity
```
Time Complexity : O(n^2) + O(nlogn)
Space Complexity : O(1)
```
## Solution (Using Binary search)

```python

class Solution(object):
    def findKthNumber(self, m, n, k):
        # function f gives the total numbers which are less than and equal to target present in matrix.
        def f(target):
            return sum(min(target//i,n) for i in range(1,m+1))
            
        lo,hi = 0,(m+1)*(n+1)
        
        while lo<hi:
            
            mid = (lo+hi)//2
            
            if f(mid) < k:
                lo = mid+1
            else:
                hi = mid
                
        return hi
```
## Complexity
```
Time Complexity : O(M * log(M * N))
Space Complexity : O(1)
```

## Geeksforgeeks
[Kth Smallest Number in Multiplication Table](https://practice.geeksforgeeks.org/problems/kth-smallest-number-in-multiplication-table/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Binary%20Search&sortBy=submissions)

