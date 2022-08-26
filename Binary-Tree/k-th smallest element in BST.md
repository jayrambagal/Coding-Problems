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
class Solution:
    # Return the Kth smallest element in the given BST 
    def KthSmallestElement(self, root, K): 
        
        ans = []
        return self.solve(root,K,ans)
        
    def solve(self,root,K,ans):
        
        if root is None:
            return 
        
        ans.append(root.data)
        self.solve(root.left,K,ans)
        
        self.solve(root.right,K,ans)
        
        ans.sort()
        
        if len(ans)<K:
            return -1
        return ans[K-1]
```
#### Complexity
```bash
Time Complexity : O(n) + O(nlogn)
Space Complexity : O(n)

```

## Geeksforgeeks
[k-th smallest element in BST](https://practice.geeksforgeeks.org/problems/find-k-th-smallest-element-in-bst/1?page=2&company[]=Google&sortBy=submissions)
