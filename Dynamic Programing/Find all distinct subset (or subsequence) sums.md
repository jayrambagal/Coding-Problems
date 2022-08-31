## Find all distinct subset (or subsequence) sums
Given a set of integers, find all distinct sums that can be generated from the subsets of the given sets.
 
## Example 1


```bash
Input: nums = {1,2,3}
Output: {0,1,2,3,4,5,6}
Explanation: Seven distinct sum can be calculated
which are 0, 1, 2, 3, 4, 5 and 6.
0 if we do not choose any number.
1 if we choose only 1.
2 if we choose only 2.
3 if we choose only 3.
4 if we choose 1 and 3.
5 if we choose 2 and 3.
6 if we choose 1, 2 and 3
```

## Solution
```python
class Solution:
	def DistinctSum(self, arr):
	    n = len(nums)
        Sum = sum(arr)
         
        dp = [[False for i in range(Sum + 1)]
                     for i in range(n + 1)]
                      
        for i in range(n + 1):
            dp[i][0] = True
     
        for i in range(1, n + 1):
     
            dp[i][arr[i - 1]] = True
     
            for j in range(1, Sum + 1):
                 
                if (dp[i - 1][j] == True):
                    dp[i][j] = True
                    dp[i][j + arr[i - 1]] = True
        ans = []            
        for j in range(Sum + 1):
            if (dp[n][j] == True):
                ans.append(j)
                
        return ans
```
	    
    

```bash
Time Complexity : O(n*sum)
Space Complexity : O(n*sum)
```
## geeksforgeeks
[Find all distinct subset (or subsequence) sums](https://practice.geeksforgeeks.org/problems/find-all-distinct-subset-or-subsequence-sums4424/1)
