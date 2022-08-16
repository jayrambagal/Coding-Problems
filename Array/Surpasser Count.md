## Surpasser Count
An element Y is said to be the surpasser of element X if it is a greater element on the right of X. ie, if X = arr[i] and Y = arr[j], i<j and Arr[i] < Arr[j]. 
Given an array of size N containing distinct integers, find the number of surpassers for each of its elements.


## Example 
```bash
Input:
N = 5
Arr[] = {4, 5, 1, 2, 3}

Output: 1 0 2 1 0

```
## Solution (brutforce)

```python
class Solution:
    def findSurpasser(self, arr, n):
        
        ans = []
        
        for i in range(n):
            count = 0
            for j in range(i+1,n):
                
                if arr[i]<arr[j]:
                    count+=1
                    
            ans.append(count)
            
        return ans
```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity : O(n)

```
## Solution (optimized)

```python


```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)

```

## Geeksforgeeks 
[Surpasser Count](https://practice.geeksforgeeks.org/problems/surpasser-count0615/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Google&category[]=Arrays&sortBy=submissions)
