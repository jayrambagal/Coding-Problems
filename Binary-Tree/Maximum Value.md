## Maximum Value
Given a binary tree, find the largest value in each level.

   
## Example 1


```bash
Input:
        4
       / \
      9   2
     / \   \
    3   5   7 
Output:
4 9 7
Explanation:
At 0 level, values of nodes are {4}
                 Maximum value is 4
At 1 level, values of nodes are {9,2}
                 Maximum value is 9
At 2 level, values of nodes are {3,5,7}
                 Maximum value is 7

```


## Solution 1 

```Python
from collections import deque
class Solution:
    def maximumValue(self,node):
        # code here
        d=deque()
        maxes=[]
        d.append(node)
        while d:
            n=len(d)
            temp=-float("inf")
            for i in range(n):
                ele=d.popleft()
                temp=max(temp,ele.data)
                if ele.right:
                    d.append(ele.right)
                if ele.left:
                    d.append(ele.left)
            maxes.append(temp)
        return maxes
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Maximum Value](https://practice.geeksforgeeks.org/problems/ec277982aea7239b550b28421e00acbb1ea03d2c/1)
