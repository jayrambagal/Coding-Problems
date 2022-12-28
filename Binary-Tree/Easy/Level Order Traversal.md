## Level order traversal
Given a binary tree, find its level order traversal.
Level order traversal of a tree is breadth-first traversal for the tree.
  
## Example 1


```bash
IInput:
    1
  /   \ 
 3     2
Output:1 3 2

Input:
        10
     /      \
    20       30
  /   \
 40   60
Output:10 20 30 40 60

```

## Solution 1 

```Python
class Solution:
    def levelOrder(self,root ):
        
        q = [root]
        ans = []
        while q:
            node = q.pop(0)
            ans.append(node.data)
            if node.left != None:
                q.append(node.left)
            if node.right != None:
                q.append(node.right)
        return ans
        
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## GeeksforGeeks

[Level order traversal](https://practice.geeksforgeeks.org/problems/level-order-traversal/1?page=1&difficulty[]=0&category[]=Tree&sortBy=submissions)
