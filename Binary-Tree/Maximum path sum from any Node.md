## Maximum path sum from any node
Given a binary tree, the task is to find the maximum path sum. The path may start and end at any node in the tree. 

   
## Example 1


```bash
Input:
     10
    /  \
   2   -25
  / \  /  \
 20 1  3  4
Output: 32
Explanation: Path in the given tree goes
like 10 , 2 , 20 which gives the max
sum as 32.


```

## Solution 1 

```Python
import sys
class Solution:
   
    def findMaxSum(self, root): 
        
        ans = - sys.maxsize

        def dfs(root):
            nonlocal ans
            if not root:
                return 0
            l = dfs(root.left)
            r = dfs(root.right)
            v = root.data
            ans = max(ans, max([v, l + r + v, l + v, r + v]))
            return max([v, l + v, r + v])

        dfs(root)
        return ans
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## GeeksforGeeks

[Maximum path sum from any node](https://practice.geeksforgeeks.org/problems/maximum-path-sum-from-any-node/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Google&category[]=Tree&sortBy=submissions)
