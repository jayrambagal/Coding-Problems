## Maximum Path Sum between 2 Leaf Nodes
Given a binary tree in which each node element contains a number. 

Find the maximum possible path sum from one leaf node to another leaf node.

Note: Here Leaf node is a node which is connected to exactly one different node. 

   
## Example 1


```bash
Input:      
           3                               
         /    \                          
       4       5                     
      /  \      
    -10   4                          
Output: 16
Explanation:
Maximum Sum lies between leaf node 4 and 5.
4 + 4 + 3 + 5 = 16.


```

## Solution 1 

```Python
class Solution:        
    def maxPathSum(self, root):
        res = [-float('inf')]
        ans = self.maxPathSumUtil(root, res)
        
        if not root.left or not root.right:
            res[0] = max(res[0], ans)
        return res[0]
       
       
    def maxPathSumUtil(self,root, res):
    
        if root is None:
            return 0
            
        ls = self.maxPathSumUtil(root.left, res)
        rs = self.maxPathSumUtil(root.right, res)
       
        if root.left is not None and root.right is not None:
            res[0] = max(res[0], ls + rs + root.data)
            return max(ls, rs) + root.data
    
        if root.left is None:
            return rs + root.data
        else:
            return ls + root.data
        return root.data+max(ls,rs)
```
`
## GeeksforGeeks

[Maximum Path Sum between 2 Leaf Nodes](https://practice.geeksforgeeks.org/problems/maximum-path-sum/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
