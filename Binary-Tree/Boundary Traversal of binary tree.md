## Boundary Traversal of binary tree

```
Given a Binary Tree, find its Boundary Traversal. The traversal should be in the following order: 

1. Left boundary nodes:
defined as the path from the root to the left-most node ie- the leaf node you 
could reach when you always travel preferring the left subtree over the right subtree.

2. Leaf nodes: 
All the leaf nodes except for the ones that are part of left or right boundary.

3. Reverse right boundary nodes: 
defined as the path from the right-most node to the root. The right-most node is the 
leaf node you could reach when you always travel preferring the right subtree over 
the left subtree. Exclude the root from this as it was already included in the traversal 
of left boundary nodes.

Note: If the root doesn't have a left subtree or right subtree, then the root itself is the left or right boundary. 
```




## Example 
```bash
Input:
        1 
      /   \
     2     3  
    / \   / \ 
   4   5 6   7
      / \
     8   9
   
Output: 1 2 4 8 9 6 7 3
Explanation:

```
## Solution 

```python
class Solution:
    def printBoundaryView(self, root):
        ans = []
    
        if(root == None):
            return ans
    
        ans.append(root.data)
        self.leftBoundary(root.left, ans)
        self.leafNodes(root.left, ans)
        self.leafNodes(root.right, ans)
        self.rightBoundary(root.right, ans)
    
        return ans
        
    def leftBoundary(self,root, ans):
        if(root == None or (root.left == None and root.right == None)):
            return
    
        ans.append(root.data)
    
        if(root.left != None):
            self.leftBoundary(root.left, ans)
        else:
            self.leftBoundary(root.right, ans)
    
    
    def rightBoundary(self,root, ans):
        if(root == None or (root.left == None and root.right == None)):
            return
    
        if(root.right != None):
            self.rightBoundary(root.right, ans)
        else:
            self.rightBoundary(root.left, ans)
    
        ans.append(root.data)
    
    
    def leafNodes(self,root, ans):
        if(root == None):
            return
    
        if(root.left == None and root.right == None):
            ans.append(root.data)
            return
    
        self.leafNodes(root.left, ans)
        self.leafNodes(root.right, ans)
```
#### Complexity
```bash
Time Complexity : O(hight) + O(hight) + O(n) --> O(n)
Space Complexity : O(n)

```

## Geeksforgeeks
[Boundary Traversal of binary tree](https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
