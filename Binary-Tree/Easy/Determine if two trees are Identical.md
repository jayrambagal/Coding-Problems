## Determine if Two Trees are Identical
Given two binary trees, the task is to find if both of them are identical or not. 



## Example 
```bash
Input:
     1          1
   /   \      /   \
  2     3    2     3
Output: Yes
Explanation: There are two trees both
having 3 nodes and 2 edges, both trees
are identical having the root as 1,
left child of 1 is 2 and right child
of 1 is 3.
```
## Solution 

```python
class Solution:

    def isIdentical(self,root1, root2):
        
        if root1 is None and root2 is None:
            return True
            
        if root1 is not None and root2 is not None:
            
            return ((root1.data == root2.data)
                and
                self.isIdentical(root1.left, root2.left)
                and
                self.isIdentical(root1.right, root2.right))
                
        return False

```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)

```


## Geeksforgeeks

[Determine if Two Trees are Identical](https://practice.geeksforgeeks.org/problems/determine-if-two-trees-are-identical/1?page=1&difficulty[]=0&category[]=Tree&sortBy=submissions)
