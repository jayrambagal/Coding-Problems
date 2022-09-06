## Sort an array according to the other
```
Given two integer arrays A1[ ] and A2[ ] of size N and M respectively. 
Sort the first array A1[ ] such that all the relative positions of the 
elements in the first array are the same as the elements in the second array A2[ ].
See example for better understanding.
Note: If elements are repeated in the second array, consider their first occurance only.
```

## Example 
```bash
Input:
N = 11 
M = 4
A1[] = {2, 1, 2, 5, 7, 1, 9, 3, 6, 8, 8}
A2[] = {2, 1, 8, 3}
Output: 
2 2 1 1 8 8 3 5 6 7 9
Explanation: Array elements of A1[] are
sorted according to A2[]. So 2 comes first
then 1 comes, then comes 8, then finally 3
comes, now we append remaining elements in
sorted order.

```
 
## Solution
```python
class Solution:

    def relativeSort (self,arr1, n, arr2, m):
        
        freq = {}
        ans= []
        res = []
        for i in range(n):
            if arr1[i] in freq:
                freq[arr1[i]]+=1
            else:
                freq[arr1[i]] = 1
                
        for i in range(m):
            if arr2[i] in freq:
                count = freq[arr2[i]]
                
                while count:
                    ans.append(arr2[i])
                    freq[arr2[i]]-=1
                    count-=1
                    
        for i in freq:
            if freq[i] >=1:
                a = freq[i]
                while a:
                    res.append(i)
                    a-=1
                    
        res.sort()
        for i in range(len(res)):
            ans.append(res[i])
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Sort an array according to the other](https://practice.geeksforgeeks.org/problems/relative-sorting4323/1?page=1&difficulty[]=1&status[]=unsolved&curated[]=1&sortBy=submissions)
