## Minimum Swaps to Sort
Given an array of n distinct elements. Find the minimum number of swaps required to sort the array in strictly increasing order.

## Example 
```bash
Input:
nums = {10, 19, 6, 3, 5}
Output:
2
Explaination:
swap 10 with 3 and swap 19 with 5.

```

## Solution 

```python
class Solution:
    
	def minSwaps(self, nums):

        index = []

        for i in range(0,len(nums)):
            index.append([nums[i],i])
            
        index.sort() 
        i = 0
        res = 0

        while i < len(nums):
            
            if i == index[i][1]:
                i += 1
            else:
                temp = index[i][1]
                index[i], index[temp] = index[temp], index[i]
                res += 1
                
        return res
 ```
#### Complexity
```bash
Time Complexity :O(nlogn) + O(n)
Space Complexity : O(n)
```
## Geeksforgeeks
[Minimum Swaps to Sort](https://practice.geeksforgeeks.org/problems/minimum-swaps/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
