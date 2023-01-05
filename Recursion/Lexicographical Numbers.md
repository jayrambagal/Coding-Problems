## Lexicographical Numbers
Given an integer n, return all the numbers in the range [1, n] sorted in lexicographical order.

You must write an algorithm that runs in O(n) time and uses O(1) extra space. 

## Example 1


```bash
Input: n = 13
Output: [1,10,11,12,13,2,3,4,5,6,7,8,9]
```


## Solution  

```Python
class Solution:
    def lexicalOrder(self, n: int) -> List[int]:
        def dfs(i,n,ans):
            if i>n:
                return
            ans.append(i)
            
            for j in range(10):
                dfs(10*i+j,n,ans)
        ans = []
        for i in range(1,10):
            dfs(i,n,ans)
        return ans
```
### Complexity
 
```bash
Time Complexity :O(2^n) 
Space Complexity : 
```

## Geeksforgeeks
[Lexicographical Numbers](https://leetcode.com/problems/lexicographical-numbers/description/)
