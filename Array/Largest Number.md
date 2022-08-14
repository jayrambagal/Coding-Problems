## Largest Number
Given a list of non-negative integers nums, arrange them such that they form the largest number and return it.

Since the result may be very large, so you need to return a string instead of an integer.

## Example 
```bash
Input: nums = [3,30,34,5,9]
Output: "9534330"

```
## Solution (brutforce)

```python

class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        n = len(nums) 
        nums = list(map(str,nums))
        
        if n<2:
            return str(nums[0])
        
        for i in range(n):
            if nums[i]!="0":
                break
            elif i==n-1:
                return "0"
                
        
        def compare(i,y):
            return int(nums[i]+nums[j]) > int(nums[j] + nums[i])
        
        for i in range(n-1):
            j = i+1
            
            while(j<n):
                if compare(i,j):
                    pass
                else:
                    nums[i],nums[j] = nums[j],nums[i]
                    
                    
                j+=1
        ans = ""        
        for i in range(n):
            ans+=nums[i]
            
        return ans
```
#### Complexity
```bash
Time Complexity : O(n) + O(n) + O(n^2)
Space Complexity : O(1)

```
## Solution (optimized)

```python


```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)

```

## Geeksforgeeks
[Largest Number](https://leetcode.com/problems/largest-number/)

