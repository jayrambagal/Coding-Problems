## Delete nodes greater than k
Given a BST and a value k, the task is to delete the nodes having values greater than or equal to k.

   
## Example 1


```bash
Input:
    4   
   / \  
  1   9 
k = 2 
Output:
1
```

## Solution 
```python
class Solution:
    def deleteNode(self, root, k):
        if not root:
            return 
        
        if root.data >= k:
            return self.deleteNode(root.left, k)
            
        root.left = self.deleteNode(root.left, k)
        root.right = self.deleteNode(root.right, k)
        return root
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Delete nodes greater than k](https://practice.geeksforgeeks.org/problems/delete-nodes-greater-than-k/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
