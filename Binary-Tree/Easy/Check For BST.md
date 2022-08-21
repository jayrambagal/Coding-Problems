## Check for BST
Given the root of a binary tree. Check whether it is a BST or not.
Note: We are considering that BSTs can not contain duplicate Nodes.
A BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.



## Example 
```bash
Input:
   2
 /    \
1      3
Output: 1 
Explanation: 
The left subtree of root node contains node
with key lesser than the root nodes key and 
the right subtree of root node contains node 
with key greater than the root nodes key.
Hence, the tree is a BST.

```
## Solution 

```python
import sys
left_val=-sys.maxsize-1
right_val=sys.maxsize

class Solution:
   
   
   def isBST(self, root):
       
       def solve(root,left_val,right_val):
           if root==None:
               return True
               
           if not(root.data<right_val and root.data>left_val ):
               return False
               
           return ((solve(root.left,left_val,root.data)) and (solve(root.right,root.data,right_val)))

       return solve(root,left_val,right_val)

```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)

```


## Geeksforgeeks
[Check for BST](https://practice.geeksforgeeks.org/problems/check-for-bst/1?page=1&difficulty[]=0&company[]=Amazon&company[]=Microsoft&company[]=Google&category[]=Tree&sortBy=submissions)

