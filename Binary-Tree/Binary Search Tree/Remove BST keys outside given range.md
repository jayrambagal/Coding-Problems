## Remove BST keys outside given range
Given a Binary Search Tree (BST) and a range [min, max], remove all 

keys which are outside the given range. The modified tree should also be BST.

   
## Example 1


```bash
Input:
Range = [2, 6]
        14
      /    \
     4      16
    / \     /
   2   8   15
  / \  / \
 -8  3 7  10
Output:
2 3 4
Explanation:
After removing nodes outside the range, 
the resultant BST looks like:
               4
              /
             2
              \
                3 
The inorder traversal of this tree is: 2 3 4
```



## Solution (stack)
```python
class Solution:
    def removekeys(self, root, minn, maxx):
        
        if root is None:
            return
        
        root.left = self.removekeys(root.left,l,r)
        root.right = self.removekeys(root.right,l,r)
        
        if root.data < minn:
            return root.right
        elif root.data > maxx:
            return root.left
            
        return root
            
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Remove BST keys outside given range](https://practice.geeksforgeeks.org/problems/remove-bst-keys-outside-given-range/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
