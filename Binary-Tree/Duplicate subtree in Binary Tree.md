## Duplicate subtree in Binary Tree
Given a binary tree, find out whether it contains a duplicate sub-tree of size two or more, or not. 

   
## Example 1


```bash
Input : 
               1
             /   \ 
           2       3
         /   \       \    
        4     5       2     
                     /  \    
                    4    5
Output : 1
Explanation : 
    2     
  /   \    
 4     5
is the duplicate sub-tree.


Input : 
               1
             /   \ 
           2       3
Output: 0
Explanation: There is no duplicate sub-tree 
in the given binary tree.

```


## Solution 1 (hashmap)

```Python
class Solution:
   def solve(self,root,dic):
       
       if not root:
           return "$"
       st = ""
       
       if not root.left and not root.right:
           st=chr(root.data)
           return st
       
       st+= chr(root.data)
       st+= self.solve(root.left, dic)
       st+= self.solve(root.right, dic)
       if st not in dic:
           dic[st]=1
       else:
           dic[st]+=1
       return st


   def dupSub(self, root):
       dic={}
       self.solve(root, dic)
       for i in dic:
           if dic[i]>=2:
               return 1
       return 0
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Duplicate subtree in Binary Tree](https://practice.geeksforgeeks.org/problems/duplicate-subtree-in-binary-tree/1?page=1&difficulty[]=1&company[]=Google&category[]=Tree&sortBy=submissions)
