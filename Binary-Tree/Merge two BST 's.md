## Merge two BST 's

Given two BSTs, return elements of both BSTs in sorted form.




## Example 
```bash
Input:
BST1:
       5
     /   \
    3     6
   / \
  2   4  
BST2:
        2
      /   \
     1     3
            \
             7
            /
           6
Output: 1 2 2 3 3 4 5 6 6 7
Explanation: 
After merging and sorting the
two BST we get 1 2 2 3 3 4 5 6 6 7.

```
## Solution 

```python
class Solution:
    def merge(self, root1, root2):
        
        arr1 = []
        arr2 = []
        
        self.solve(root1,arr1)
        self.solve(root2,arr2)
        
        arr1.extend(arr2)
        arr1.sort()
        return arr1
        
        
    def solve(self,root,arr):
        
        if root is None:
            return arr
            
        arr.append(root.data)
        self.solve(root.left,arr)
        self.solve(root.right,arr)
        
        return arr
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(1)

```

## Geeksforgeeks
[Merge two BST 's](https://practice.geeksforgeeks.org/problems/merge-two-bst-s/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Google&category[]=Tree&sortBy=submissions)
