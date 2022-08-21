## Root to leaf paths sum
Given a binary tree of N nodes, where every node value is a number.

Find the sum of all the numbers which are formed from root to leaf paths.

   
## Example 1


```bash
Input :      
           6                               
         /   \                          
        3     5                      
      /   \     \
     2    5      4             
        /  \                        
       7    4  

Output: 13997

Explanation :
There are 4 leaves, hence 4 root to leaf paths:
Path                      Number
6->3->2                   632
6->3->5->7                6357
6->3->5->4                6354
6->5>4                    654   
Answer = 632 + 6357 + 6354 + 654 = 13997 


```

## Solution 1 

```Python
def treePathSum(root):
    
    return sumNumbers(root,0)
    
def sumNumbers(root,num):
    if root == None:
        
        return 0
        
    num = num*10 + root.data
        
    if root.left == None and root.right == None:
        return num
        
    return sumNumbers(root.left,num) + sumNumbers(root.right,num)
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## GeeksforGeeks

[Root to leaf paths sum](https://practice.geeksforgeeks.org/problems/root-to-leaf-paths-sum/1?page=1&difficulty[]=0&difficulty[]=1&difficulty[]=2&company[]=Google&category[]=Tree&sortBy=submissions)
