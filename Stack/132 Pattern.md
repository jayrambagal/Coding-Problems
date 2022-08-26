## 132 Pattern

Given an array of n integers nums, a 132 pattern is a subsequence of three 

integers nums[i], nums[j] and nums[k] such that i < j < k and nums[i] < nums[k] < nums[j].

Return true if there is a 132 pattern in nums, otherwise, return false.

#### Example
```bash
Input: nums = [1,2,3,4]
Output: false
Explanation: There is no 132 pattern in the sequence.

Input: nums = [3,1,4,2]
Output: true
Explanation: There is a 132 pattern in the sequence: [1, 4, 2].

```
### Solution 

```python
class Solution:
    def find132pattern(self, nums: List[int]) -> bool:
        
        n = len(nums)
        
        for i in range(n-2):
            for j in range(i+1,n-1):
                for k in range(j+1,n):
                    
                    if nums[i] < nums[k] < nums[j]:
                        return True
                    
        return False
        
```
### Complexity
```bash
Time Complexity = O(n^3)
Space Complexity = O(1) 
```

## Leetcode       
[132 Pattern](https://leetcode.com/problems/132-pattern/)
