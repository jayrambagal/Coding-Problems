## Sum Tree
Given a Binary Tree. Return true if, for every node X in the tree other than the leaves,

its value is equal to the sum of its left subtree's value and its right subtree's value. Else return false.

An empty tree is also a Sum Tree as the sum of an empty tree can be considered to be 0. A leaf node is also considered a Sum Tree.

   
## Example 1


```bash
Input:

          10
        /    \
      20      30
    /   \ 
   10    10

Output: 0
Explanation:
The given tree is not a sum tree.
For the root node, sum of elements
in left subtree is 40 and sum of elements
in right subtree is 30. Root element = 10
which is not equal to 30+40.

Input:
    3
  /   \    
 1     2

Output: 1
Explanation:
The sum of left subtree and right subtree is
1 + 2 = 3, which is the value of the root node.
Therefore,the given binary tree is a sum tree.

```


## Solution 1 

```Python
class Solution:
    
    def isSumTree(self,root):
        self.solve(root)
        return self.check
    
    check = True
    
    def solve(self,root):
        if root is None:
            return 0
            
        if root.left is None and root.right is None: # leaf node
            return root.data
            
        left = self.solve(root.left)
        right = self.solve(root.right)
        
        if root.data != left + right:    # if any node in binary tree (except leaf node) 
                                        #is not equal to additon of its left and right node then return false
            self.check = False
            return 0
            
        return root.data + left + right  # return the addition of root node + root.left +roo.right
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Sum Tree](https://practice.geeksforgeeks.org/problems/sum-tree/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
