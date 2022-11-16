## Sum of Beauty of All Substrings
Given a string S, return the sum of beauty of all its substrings.

The beauty of a string is defined as the difference in frequencies between the most frequent and least frequent characters.

For example, the beauty of string "aaac" is 3 - 1 = 2.

## Example 
```bash
Input:
S = "aaac"
Output:
3
Explanation: The substrings with non - zero beauty are ["aaac","aac"] where beauty of "aaac" is 2 and beauty of "aac" is 1.

Input:
S = "geeks"
Output:
5

```

## Solution
```python
class Solution:
    def beautySum(self, s):
        ans = 0
        for i in range(len(s)):
            freq = {}
            for j in range(i,len(s)):
                try:
                    freq[s[j]]+=1
                except:
                    freq[s[j]]=1
                    
                maxi = max(freq.values())
                mini = min(freq.values())
                
                ans+=(maxi-mini)
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(n)
```

## Geeksforgeeks
[Sum of Beauty of All Substrings](https://practice.geeksforgeeks.org/problems/sum-of-beauty-of-all-substrings-1662962118/1)
