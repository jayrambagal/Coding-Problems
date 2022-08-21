## Level order traversal
Given a binary tree, find its level order traversal.
Level order traversal of a tree is breadth-first traversal for the tree.
  
## Example 1


```bash
IInput:
    1
  /   \ 
 3     2
Output:1 3 2

Input:
        10
     /      \
    20       30
  /   \
 40   60
Output:10 20 30 40 60

```

## Solution 1 

```Python
class Solution:
    def levelOrder(self,root ):
        
        ans = []
        q = deque()
        q.append(root)
        
        while q:     # check queue is not empty
            for i in range(len(q)):
                node = q.popleft()
                
                if node: # check node is not empty
                    ans.append(node.data)
                    q.append(node.left)
                    q.append(node.right)
        return ans
        
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## GeeksforGeeks

[Level order traversal](https://practice.geeksforgeeks.org/problems/level-order-traversal/1?page=1&difficulty[]=0&category[]=Tree&sortBy=submissions)
