## Longest Arithmetic Subsequence of Given Difference
Given an integer array arr and an integer difference, return the length of the longest subsequence in arr which is an arithmetic sequence such that the difference between adjacent elements in the subsequence equals difference.

A subsequence is a sequence that can be derived from arr by deleting some or no elements without changing the order of the remaining elements.
## Example
```bash
Input: arr = [1,2,3,4], difference = 1
Output: 4
Explanation: The longest arithmetic subsequence is [1,2,3,4].

```
## Approach
![PXL_20220820_121832245 1](https://user-images.githubusercontent.com/94613732/185733019-bd14a8bb-b20f-4823-bb48-cd22a7d890ad.jpg)

## Solution 1 (Using Hashmap)

```Python
class Solution:
    def longestSubsequence(self, arr: List[int], difference: int) -> int:
        
        d = defaultdict(int)
        
        for num in arr:
            if num - difference in d:
                d[num] =  d[num - difference] + 1
            else:
                d[num] = 1
                
        return max((d[x] for x in d))
```

### Complexity
 
```bash
Time Complexity: O(n)
Space Complexity: O(n)
```





## Leetcode
[Longest Arithmetic Subsequence of Given Difference](https://leetcode.com/problems/longest-arithmetic-subsequence-of-given-difference/)
