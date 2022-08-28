## Min distance between two given nodes of a Binary Tree

Given a binary tree and two node values your task is to find the minimum distance between them.

## Example 
```bash
Input:
        1
      /  \
     2    3
a = 2, b = 3
Output: 2
Explanation: The tree formed is:
       1
     /   \ 
    2     3
We need the distance between 2 and 3.
Being at node 2, we need to take two
steps ahead in order to reach node 3.
The path followed will be:
2 -> 1 -> 3. Hence, the result is 2.  
```
## Solution 

```python
class Solution:
    def findDist(self,root,a,b):
        
        lca1 = self.lca(root,a,b)
        
        h1 = self.height(lca1,a)
        h2 = self.height(lca1,b)
        return h1+h2
        
    # finding the lowest common ansester of the two given nodes
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
    
    
    # Finding the height of given Nodes
    def height(self,root,x):
        if root is None:
            return 1e9
        if root.data == x:
            return 0
            
        return 1+min(self.height(root.left,x),self.height(root.right,x))
```
#### Complexity
```bash
Time Complexity : O()
Space Complexity : O()

```

## Geeksforgeeks
[Min distance between two given nodes of a Binary Tree](https://practice.geeksforgeeks.org/problems/min-distance-between-two-given-nodes-of-a-binary-tree/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
