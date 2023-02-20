## Sum equals to Sum
Given an array A of N integers. The task is to find if there are two pairs (a, b) and (c, d) such that a+b = c+d.

## Example 
```bash
Input:N=7 A[] = {3, 4, 7, 1, 2, 9, 8} Output: 1

Explanation:(3, 7) and (9, 1) are the pairs whosesum are equal.  
```

## Solution 

```python
class Solution:
    def findPairs(self, arr, n): 
        
        freq = {}
        
        for i in range(n-1):
            for j in range(i+1,n):
                
                summ = arr[i]+arr[j]
                
                if summ in freq:
                    return 1
                else:
                    freq[summ] = 1
        return 0
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(n^2)
```
## Geeksforgeeks
[Sum equals to Sum](https://practice.geeksforgeeks.org/problems/sum-equals-to-sum4006/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
