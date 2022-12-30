## Subsets II
Given an integer array nums that may contain duplicates, return all possible 
subsets
 (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

## Example 1


```bash
Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
```


## Solution  

```Python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        ans = set()
        out = []
        
        self.solve(nums,ans,out,0)
        ans = list(ans)
        return ans
        
    def solve(self,nums,ans,out,ind):
        
        if ind==len(nums):
            ans.add(tuple(out))
            return 
        for i in range(ind,len(nums)):
            if i>ind and nums[i]==nums[i-1]:
                continue
            self.solve(nums,ans,out,ind+1)
            out.append(nums[ind])
            self.solve(nums,ans, out,ind+1)
            out.pop()
```
### Complexity
 
```bash
Time Complexity : O(nlogn) +  O(2^n) * k   k is the len(out)
Space Complexity : 
```

## Geeksforgeeks
[Subsets II](https://leetcode.com/problems/subsets-ii/)
