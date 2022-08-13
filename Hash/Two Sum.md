## Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.



## Example 
```bash
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

```
## Solution (Brut Force)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        n=len(nums)
        ans = []
        for i in range(0,n):
            for j in range(i+1,n):
                if target-nums[i] == nums[j] :
                    ans.append(i)
                    ans.append(j)
                    
        return ans

```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity : O(n)

```

## Solution (Using Dict)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        
        n=len(nums)
        ans = []
        hash_map = {}
    
        for i in range(0,n):
            hash_map[nums[i]] = i
                
        for i in range(len(nums)):
            if target-nums[i] in hash_map:
                if hash_map[target-nums[i]] != i:
                    return [i, hash_map[target-nums[i]]]
        return [0,0]
        
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Two Sum](https://leetcode.com/problems/two-sum/)

