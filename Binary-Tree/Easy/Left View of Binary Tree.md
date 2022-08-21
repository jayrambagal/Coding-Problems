## Left View of Binary Tree
visited from Left side. The task is to complete the function leftView(), which accepts root of the tree as argument.

Left view of following tree is 1 2 4 8.

```
          1
       /     \
     2        3
   /     \    /    \
  4     5   6    7
   \
     8   
 ```    
## Example 1


```bash
Input:
Input:
   1
 /  \
3    2
Output: 1 3


```

## Solution 1 (Recursion)

```Python
def LeftView(root):
    ans=[]
    def leftview(root,level):
        if not root:
            return
        if len(ans)==level:
            ans.append(root.data)
        
        
        leftview(root.left,level+1)
        leftview(root.right,level+1)
        
    leftview(root,0)
    
    return ans
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## GeeksforGeeks

[Left View of Binary Tree](https://practice.geeksforgeeks.org/problems/left-view-of-binary-tree/1?page=1&difficulty[]=0&category[]=Tree&sortBy=submissions)
