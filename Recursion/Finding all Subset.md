## Subset
Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.
## Example 1


```bash
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]


Input: nums = [0]
Output: [[],[0]]

```

## Solution 1 (Recursion)

```Python
class Solution:
    
    def subsets(self, nums: List[int]) -> List[List[int]]:
        ans = []
        
        def solve(nums, pos, op):
            if pos==len(nums):
                ans.append(op)
                return
            
            solve(nums, pos+1, op)
            
            solve(nums, pos+1, op+[nums[pos]])
            
        solve(nums, 0, [])
        
        return ans
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Subset](https://leetcode.com/problems/subsets/)
