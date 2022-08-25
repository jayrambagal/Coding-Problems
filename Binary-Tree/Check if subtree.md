## Check if subtree
Given two binary trees with head reference as T and S having at most N nodes. The task is to check if S is present as subtree in T.
A subtree of a tree T1 is a tree T2 consisting of a node in T1 and all of its descendants in T1.

   
## Example 1


```bash
Input:
T:      1          S:   3
      /   \            /
     2     3          4
   /  \    /
  N    N  4
Output: 1 
Explanation: S is present in T

```


## Solution 1 

```Python
class Solution:
    def isSubTree(self, T, S):
        
        if S is None:
            return True
     
        if T is None:
            return False
     
        if (self.areIdentical(T, S)):
            return True
     
        return self.isSubTree(T.left, S) or self.isSubTree(T.right, S)
                    
    def areIdentical(self,root1, root2):
         
        if root1 is None and root2 is None:
            return True
        if root1 is None or root2 is None:
            return False
     
        return (root1.data == root2.data and
                self.areIdentical(root1.left , root2.left)and
                self.areIdentical(root1.right, root2.right)
                )
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Check if subtree](https://practice.geeksforgeeks.org/problems/check-if-subtree/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Tree&sortBy=submissions)
