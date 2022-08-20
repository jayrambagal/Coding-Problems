## Longest Arithmetic Subsequence of Given Difference
Given an integer array arr and an integer difference, return the length of the longest subsequence in arr which is an arithmetic sequence such that the difference between adjacent elements in the subsequence equals difference.

A subsequence is a sequence that can be derived from arr by deleting some or no elements without changing the order of the remaining elements.
## Example
```bash
Input: arr = [1,2,3,4], difference = 1
Output: 4
Explanation: The longest arithmetic subsequence is [1,2,3,4].

```

## Solution 1 (Brut force)

```Python
class Solution:
    def lengthOfLongestAP(self, arr, n):
        
        if n<=2:
            return n
        
        ans = 0
        
        for i in range(n):
            for j in range(i+1,n):
                
                ans = max(ans,2+self.solve(i,arr[j]-arr[i],arr))
                
        return ans
        
    def solve(self,index,diff,arr):
        
        if index<0:
            return 0
        res = 0    
        for j in range(index-1,-1,-1):
            
            if arr[index]-arr[j] == diff:
                res = max(res,1+self.solve(j,diff,arr))
                
        return res
```

![IMG_20220820_110334 1](https://user-images.githubusercontent.com/94613732/185730623-09441855-1b3a-48cb-a7e1-3c9c70f07848.jpg)
![IMG_20220820_110320 1](https://user-images.githubusercontent.com/94613732/185730657-7474c4aa-2a29-4e3d-aeee-c9b347623f2c.jpg)
### Complexity
 
```bash
Time Complexity: O()
Space Complexity: O()
```
## Solution 2 (Tabulation)

```Python
from collections import defaultdict

class Solution:
    
    def lengthOfLongestAP(self, arr, n):
        
        if n<=2:
            return n
        res = 0
        
        memo = defaultdict(lambda: defaultdict(lambda: 2))
        
        for i in range(1, n):
            for j in range(i):
                
                diff = arr[i]-arr[j]
                if diff in memo[j]:
                    memo[i][diff] = memo[j][diff]+1
                res = max(res, memo[i][diff])
                
        return res
```
 
```bash
Time Complexity: O(n^2)
Space Complexity: O(n^2)
```




## Leetcode
[Longest Arithmetic Subsequence of Given Difference](https://practice.geeksforgeeks.org/problems/longest-arithmetic-progression1019/1)
