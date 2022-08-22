## Count BST nodes that lie in a given range
Given a Binary Search Tree (BST) and a range l-h(inclusive), count the number of nodes in the BST that lie in the given range.

1.The values smaller than root go to the left side

2.The values greater and equal to the root go to the right side
## Example 1


```bash
Input:
      10
     /  \
    5    50
   /    /  \
  1    40  100
l = 5, h = 45
Output: 3
Explanation: 5 10 40 are the node in the
range


Input:
     5
    /  \
   4    6
  /      \
 3        7
l = 2, h = 8
Output: 5
Explanation: All the nodes are in the
given range.

```


## Solution 1 

```Python
class Solution:
    def getCount(self,root,low,high):
        count = [0]
        return self.solve(root,low,high,count)
        
    def solve(self,root,low,high,count):
        if root is None:
            return
        
        if root.data >=low and root.data<=high:
            count[0]+=1
        self.solve(root.left,low,high,count)
        
        
        self.solve(root.right,low,high,count)
        
        return count[0]
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Count BST nodes that lie in a given range](https://practice.geeksforgeeks.org/problems/count-bst-nodes-that-lie-in-a-given-range/1?page=1&difficulty[]=1&company[]=Google&category[]=Tree&sortBy=submissions)
