## Jump Game

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

## Example 
```bash
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.

Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.

```
## Solution (brutforce)

```python

```
#### Complexity
```bash
Time Complexity : 
Space Complexity : 

```
## Solution (optimized)

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        n = len(nums)
        last_index = n-1
        for i in range(n-1,-1,-1):
            if i + nums[i] >= last_index:
                last_index = i
                
        if last_index == 0:
            return True
        else:
            return False

```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)

```

## LeetCode
[Jump Game](https://leetcode.com/problems/jump-game/)
