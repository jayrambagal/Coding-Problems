## Permutations
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

## Example 1


```bash
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```


## Solution  

```Python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        def solve(ans,out,freq):
            if len(out)>=len(nums):
                ans.append(out[::])
                return  
            for i in range(len(nums)):
                if nums[i] not in freq:
                    freq[nums[i]]=1
                    out.append(nums[i])
                    solve(ans,out,freq)
                    out.pop()
                    del freq[nums[i]]
        ans = []
        out = []
        freq = {}
        solve(ans,out,freq)
        return ans
```
### Complexity
 
```bash
Time Complexity : O(!n*n) 
Space Complexity : O(n) +O(n)
```

## Geeksforgeeks
[Permutations](https://leetcode.com/problems/permutations/description/)
