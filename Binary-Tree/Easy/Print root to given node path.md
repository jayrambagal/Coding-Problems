## Path to Given Node
```
Given a Binary Tree A containing N nodes.

You need to find the path from Root to a given node B.

NOTE:

No two nodes in the tree have same data values.
You can assume that B is present in the tree A and a path always exists.
```



## Example 
```bash
Input 1:

 A =

           1
         /   \
        2     3
       / \   / \
      4   5 6   7 


B = 5

Input 2:

 A = 
            1
          /   \
         2     3
        / \ .   \
       4   5 .   6


B = 1

```
## Solution 

```python
class Solution:
    
    def solve(self, A, B):
        arr = []
        if A == None:
            return arr
            
        self.solve1(A,B,arr)
        
        return arr
        
    def solve1(self,root,x,arr):
        
        if root is None:
            return False
        arr.append(root.val)
        
        if root.val == x:
            return True
            
        if self.solve1(root.left,x,arr) or self.solve1(root.right,x,arr):
            return True
        
        arr.pop()
        
        return False
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)

```

## Interviewbit
[Path to given Node](https://www.interviewbit.com/problems/path-to-given-node/)
