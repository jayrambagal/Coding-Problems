## Inorder Traversal (Iterative)
Given a binary tree. Find the inorder traversal of the tree without using recursion.




## Example 
```bash
Input:
           1
         /    \
       2       3
      /   \
    4     5
Output: 4 2 5 1 3
Explanation:
Inorder traversal (Left->Root->Right) of 
the tree is 4 2 5 1 3.
```
## Solution (Recursively)

```python
class Solution:
    def inOrder(self, root):
        if root is None:
            return []
            
        return self.inOrder(root.left) + [root.data] + self.inOrder(root.right)
```
#### Complexity
```bash
Time Complexity :  O(n)
Space Complexity : O(n)

```
## Solution (Iteratively)

```python
class Solution:
    def inOrder(self, root):
        
        stack = []
        ans = []
        
        while root or stack != []:
            
            while root:
                stack.append(root)
                root = root.left
                
            root = stack.pop()
            ans.append(root.data)
            
            root = root.right
            
        return ans
```
#### Complexity
```bash
Time Complexity :  O(n)
Space Complexity : O(n)

```

## Geeksforgeeks
[Inorder Traversal (Iterative)](https://practice.geeksforgeeks.org/problems/inorder-traversal-iterative/1?page=2&difficulty[]=1&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
