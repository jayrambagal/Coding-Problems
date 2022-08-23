## Preorder traversal (Iterative)
Given a binary tree. Find the preorder traversal of the tree without using recursion.



## Example 
```bash
Input:
           1
         /   \
        2     3
      /  \
     4    5
Output: 1 2 4 5 3
Explanation:
Preorder traversal (Root->Left->Right) of 
the tree is 1 2 4 5 3.
```
## Solution (Recursively)

```python
    def preOrder(self, root):
        
        if root is None:
            return []
            
        return [root.data] + self.preOrder(root.left) + self.preOrder(root.right)
```
#### Complexity
```bash
Time Complexity :  O(n)
Space Complexity : O(n)

```
## Solution (Iteratively)

```python
class Solution:
    def preOrder(self, root):
        
        stack = [root]
        result = []
        
        while stack != []:
            
            root = stack.pop()
            result.append(root.data)
            
            if root.right is not None:
                stack.append(root.right)
                
            if root.left is not None:
                stack.append(root.left)
                
        return result

```
#### Complexity
```bash
Time Complexity :  O(n)
Space Complexity : O(n)

```

## Geeksforgeeks
[Preorder Traversal (Iterative)](https://practice.geeksforgeeks.org/problems/preorder-traversal-iterative/1?page=2&difficulty[]=1&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
