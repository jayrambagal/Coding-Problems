## Container With Most Water
Given N non-negative integers a1,a2,....an where each represents a point at coordinate (i, ai). 

N vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i,0). 

Find two lines, which together with x-axis forms a container, such that it contains the most water.

## Example 
```bash
Input:
N = 4
a[] = {1,5,4,3}
Output: 6
Explanation: 5 and 3 are distance 2 apart.
So the size of the base = 2. Height of
container = min(5, 3) = 3. So total area
= 3 * 2 = 6.

```

## Solution 

```python
def maxArea(A,n):
    
    max_ans = 0
    
    first = 0
    last = n-1
    
    while first < last:
        max_ans = max(max_ans , min(A[first],A[last])*abs(last - first))
        
        if A[first] < A[last]:
            first+=1
        else:
            last-=1
            
    return max_ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[Container With Most Water](https://practice.geeksforgeeks.org/problems/container-with-most-water0535/1?page=2&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Strings&sortBy=submissions)
