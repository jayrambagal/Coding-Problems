## Add all greater values to every node in a BST
Given a BST, modify it so that all greater values in the given BST are added to every node.

   
## Example 1


```bash
Input:
          2
        /   \
       1     5
            /  \
           4    7
Output: 19 18 16 12 7
```


## Solution 1 

```Python
class Solution:
    def bstToGst(self, root: TreeNode) -> TreeNode:
                
        self.res = 0
        
        def traversal(root):
            if not root: return 
            
            if root.right: traversal(root.right)
            self.res += root.val
            root.val = self.res
            
            if root.left: traversal(root.left)
            
        traversal(root)
        return root
```
```bash
Time Complexity : O(n) 
Space Complexity : O(n) 
```


## GeeksforGeeks

[Add all greater values to every node in a BST](https://practice.geeksforgeeks.org/problems/add-all-greater-values-to-every-node-in-a-bst/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
