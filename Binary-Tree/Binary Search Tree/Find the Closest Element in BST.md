## Find the Closest Element in BST
Given a BST and an integer. Find the least absolute difference between any node value of the BST and the given integer.

   
## Example 1


```bash
Input:
        10
      /   \
     2    11
   /  \ 
  1    5
      /  \
     3    6
      \
       4
K = 13
Output: 2
Explanation: K=13. The node that has
value nearest to K is 11. so the answer
is 2

```


## Solution 1 

```Python
class Solution:
    def minDiff(self,root, K):
        
        if root is None:return 1e9
        
        a = self.minDiff(root.left,K)
        b = self.minDiff(root.right,K)
        c = abs(root.data - K)
        
        return min(a,b,c)
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Find the Closest Element in BST](https://practice.geeksforgeeks.org/problems/find-the-closest-element-in-bst/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
