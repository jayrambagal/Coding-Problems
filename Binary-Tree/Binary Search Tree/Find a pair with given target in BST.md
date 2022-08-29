## Find a pair with given target in BST
Given a Binary Search Tree and a target sum. Check whether there's 

a pair of Nodes in the BST with value summing up to the target sum. 

   
## Example 1


```bash
Input:
        2
      /   \
     1     3
sum = 5
Output: 1 
Explanation: 
Nodes with value 2 and 3 sum up to 5.
```


## Solution 1 

```Python
class Solution:
    def isPairPresent(self,root, target): 
        ans = []
        return self.solve(root,target,ans)
        
    def solve(self,root,x,ans):
        if root is None:return
        
        self.solve(root.left,x,ans)
        ans.append(root.data)
        self.solve(root.right,x,ans)
        
        n = len(ans)
        i = 0
        j = n-1
        
        while i<j:
            if ans[i]+ans[j] == x:
                return 1
                
            elif ans[i]+ans[j] > x:
                j-=1
            else:
                i+=1
                
       return 0
```
```bash
Time Complexity : O(n) + O(n)
Space Complexity : O(n) + O(n)
```

## GeeksforGeeks

[Find a pair with given target in BST](https://practice.geeksforgeeks.org/problems/find-a-pair-with-given-target-in-bst/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
