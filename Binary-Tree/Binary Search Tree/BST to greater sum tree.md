## BST to greater sum tree
Given a BST, transform it into greater sum tree where each

node contains sum of all nodes greater than that node.

   
## Example 1


```bash
Input:
           2
         /    \
        1      6
              /  \
             3    7
Output: 18 16 13 7 0
Explanation:
Every node is replaced with the 
sum of nodes greater than itself. 
The resultant tree is:
               16
             /    \
           18       7
                  /   \
                 13    0
```


## Solution 1 

```Python
class Solution:
    
    def transformTree(self, root):
        self.sum = 0
        def solve(root):
            if root is None:
                return
            solve(root.right)
            
            num = root.data
            root.data = self.sum
            self.sum+=num
            
            solve(root.left)
        solve(root)
```
```bash
Time Complexity : O(n) 
Space Complexity : O(n) 
```


## GeeksforGeeks

[ABST to greater sum tree](https://practice.geeksforgeeks.org/problems/bst-to-greater-sum-tree/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
