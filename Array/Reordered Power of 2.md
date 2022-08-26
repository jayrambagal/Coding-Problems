## Reordered Power of 2
You are given an integer n. We reorder the digits in any order (including the original order) such that the leading digit is not zero.

Return true if and only if we can do this so that the resulting number is a power of two.

## Example 
```bash
Input: n = 10
Output: false

Input: n = 24
Output: false

Input: n = 16
Output: True

```


## Solution 
```python
class Solution:
    def reorderedPowerOf2(self, n: int) -> bool:
        
        n1 = sorted(str(n))
        
        for i in range(30):
            ans = sorted(str(2**i))
            
            if ans == n1:
                return True
        return False
```


## Leetcode
[Reordered Power of 2](https://leetcode.com/problems/reordered-power-of-2/)
