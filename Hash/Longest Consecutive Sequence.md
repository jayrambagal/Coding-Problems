## Longest Consecative  Sequence

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.



## Example 
```bash
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

```
## Solution (Brut Force)

```python
class Solution:

    def longestConsecutive(self, nums: List[int]) -> int:
        
        nums.sort()
        # base cases
        
        n =len(nums)
        if n==0:
            return 0
        if n==1:
            return 1
            
        count = 1
        max_count = 1
        
        for i in range(n-1):
            
            if nums[i]+1==nums[i+1]:
                count+=1
                max_count = max(max_count,count)
            elif nums[i]==nums[i+1]:
                continue
            else:
                count = 1
        return max_count

```
#### Complexity
```bash
Time Complexity : O(n)+O(nlogn)
Space Complexity : O(1)

```

## Solution (hash set)
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
    
        numSet = set(nums)
        longest = 0

        for n in nums:
            if (n - 1) not in numSet:
                length = 0
                while (n + length) in numSet:
                    length += 1
                    
                longest = max(length, longest)
                
        return longest
        
```
#### Complexity
```bash
Time Complexity : O(n) + O(n) +O(n)
Space Complexity : O(n)
```

## LeetCode
[Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/submissions/)
