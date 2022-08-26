## k-th smallest element in BST

Given a BST and an integer K. Find the Kth Smallest element in the BST. 




## Example 
```bash
Input:
      2
    /   \
   1     3
K = 2
Output: 2

```
## Solution 

```python
class Solution:
    # Return the Kth smallest element in the given BST 
    def KthSmallestElement(self, root, K): 
        
        ans = []
        return self.solve(root,K,ans)
        
    def solve(self,root,K,ans):
        
        if root is None:
            return 
       
        self.solve(root.left,K,ans)
        ans.append(root.data)
        self.solve(root.right,K,ans)
        
        if len(ans)<K:
            return -1
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)

```

## Geeksforgeeks
[k-th smallest element in BST](https://practice.geeksforgeeks.org/problems/find-k-th-smallest-element-in-bst/1?page=2&company[]=Google&sortBy=submissions)
