## Preorder to BST
Given an array arr[] of N nodes representing preorder traversal of some BST. 

You have to build the exact BST from it's given preorder traversal.

In Pre-Order traversal, the root node is visited before the left child and right child nodes.

   
## Example 1


```bash
Input:
N = 5
arr[]  = {40,30,35,80,100}
Output: 35 30 100 80 40
Explanation: PreOrder: 40 30 35 80 100
InOrder: 30 35 40 80 100
Therefore, the BST will be:
              40
           /      \
         30       80
           \        \   
           35      100
Hence, the postOrder traversal will
be: 35 30 100 80 40
```


## Solution (brut)

```Python
def post_order(pre, size) -> Node:
    
    root = Node(pre[0])
    
    for i in pre:
        solve(root,i)
    return root
    
def solve(root,x):
    if root is None:
        root = Node(x)
        return root
    if root.data > x:
        root.left = solve(root.left,x)
        
    elif root.data < x:
        root.right = solve(root.right,x)
    
    return root
```
```bash
Time Complexity : O(n^2) 
Space Complexity : O() 
```


## GeeksforGeeks

[Preorder to BST](https://practice.geeksforgeeks.org/problems/preorder-to-postorder4423/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
