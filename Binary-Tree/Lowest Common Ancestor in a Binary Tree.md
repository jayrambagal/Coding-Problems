## Lowest Common Ancestor in a Binary Tree

Given a Binary Tree with all unique values and two nodes value, n1 and n2. The task is to find the lowest common ancestor of the given two nodes. 

We may assume that either both n1 and n2 are present in the tree or none of them are present.

LCA: It is the first common ancestor of both the nodes n1 and n2 from bottom of tree.




## Example 
```bash
Input:
n1 = 2 , n2 = 3  
       1 
      / \ 
     2   3
Output: 1
Explanation:
LCA of 2 and 3 is 1.

Input:
n1 = 3 , n2 = 4
           5    
          /    
         2  
        / \  
       3   4
Output: 2
Explanation:
LCA of 3 and 4 is 2. 
```
## Solution 

```python
class Solution:
    def lca(self,root, n1, n2):
       
	    if root is None:
		    return None
		    
	    if root.data == n1 or root.data == n2:
		    return root

	    left = self.lca(root.left, n1, n2)
	    right = self.lca(root.right, n1, n2)

	    if left is None:
	        return right
		elif right is None:
		    return left
		else:
		    return root
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)

```

## Geeksforgeeks
[Lowest Common Ancestor in a Binary Tree](https://practice.geeksforgeeks.org/problems/lowest-common-ancestor-in-a-binary-tree/1?page=1&difficulty[]=1&company[]=Google&category[]=Tree&sortBy=submissions)
