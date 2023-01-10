## Russian Doll Envelopes

You are given a 2D array of integers envelopes where envelopes[i] = [wi, hi] represents the width and the height of an envelope.

One envelope can fit into another if and only if both the width and height of one envelope are greater than the other envelope's width and height.

Return the maximum number of envelopes you can Russian doll (i.e., put one inside the other).

Note: You cannot rotate an envelope.

#### Example
```bash
Input: envelopes = [[5,4],[6,4],[6,7],[2,3]]
Output: 3
Explanation: The maximum number of envelopes you can Russian doll is 3 ([2,3] => [5,4] => [6,7]).
```

### Solution 

```python
class Solution:
    def maxEnvelopes(self, envelopes: List[List[int]]) -> int:
        n = len(envelopes)
        if n==1:
            return 1
        envelopes.sort()
        dp = [0]*(n)
        dp[0] = 1
        max_count = 0
        for i in range(1,n):
            count = 1
            for j in range(i):
                if envelopes[i][1]>envelopes[j][1] and envelopes[i][0]!=envelopes[j][0] :
                    count = max(count,dp[j]+1)
            dp[i] = count
            max_count = max(max_count,count)
        return max_count 

        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+O(n) 
```


[Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/description/)
