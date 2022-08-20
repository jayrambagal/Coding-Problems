## Longest Arithmetic Progression
Given an array called A[] of sorted integers having no duplicates, find the length of the Longest Arithmetic Progression (LLAP) in it.
## Example
```bash
Input:
N = 6
set[] = {1, 7, 10, 13, 14, 19}
Output: 4
Explanation: The longest arithmetic 
progression is {1, 7, 13, 19}.

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




## Geeksforgeeks
[Longest Arithmetic Progression](https://practice.geeksforgeeks.org/problems/longest-arithmetic-progression1019/1)
