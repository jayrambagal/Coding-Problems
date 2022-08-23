## Height of Binary Tree
Given a binary tree, find its height.

   
## Example 1


```bash
Input:
     1
    /  \
   2    3
Output: 2

```


## Solution 1 

```Python
class Solution:
    #Function to find the height of a binary tree.
    def height(self, root):
        
        if root is None:
            return 0
            
        left = self.height(root.left)
        right = self.height(root.right)
        
        
        return max(left,right)+1
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Height of Binary Tree](https://practice.geeksforgeeks.org/problems/height-of-binary-tree/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
