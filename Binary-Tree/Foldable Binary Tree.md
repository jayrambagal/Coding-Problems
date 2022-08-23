## Foldable Binary Tree

```
Given a binary tree, check if the tree can be folded or not. A tree can be folded if left and righ
t subtrees of the tree are structure wise same. An empty tree is considered as foldable.
Consider the below trees:
(a) and (b) can be folded.
(c) and (d) cannot be folded.

(a)
       10
     /    \
    7      15
     \    /
      9  11
(b)
        10
       /  \
      7    15
     /      \
    9       11
(c)
        10
       /  \
      7   15
     /    /
    5   11
(d)
         10
       /   \
      7     15
    /  \    /
   9   10  12
```




## Example 
```bash
Input:
     10
    /    \
   7     15
 /  \   /  \
N   9  11   N
Output:Yes
Explaination:Structure of every left and right subtree are same. 

Input:
      10
    /    \
   7     15
 /  \   /  \
5   N  11   N
Output: No
Explaination: 7's left child is not NULL and right child is NULL. That's why the tree is not foldable. 

```
## Solution 

```python
def IsFoldable(root):
    if root is None:
        return True
        
    return solve(root,root)
    
def solve(root1,root2):
    
    if root1 is None:
        return root2 == None
    elif root2 is None:
        return root1==None
        
    else:
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(1)

```

## Geeksforgeeks
[Foldable Binary Tree](https://practice.geeksforgeeks.org/problems/foldable-binary-tree/1)
