## Maximum sum of Non-adjacent nodes
Given a binary tree with a value associated with each node, we need to choose a subset of these nodes such that sum of

chosen nodes is maximum under a constraint that no two chosen node in subset should be directly connected that is,

if we have taken a node in our sum then we can’t take its any children or parents in consideration and vice versa. 

   
## Example 1


```bash
Input:
Input:
     11
    /  \
   1    2
Output: 11
Explanation: The maximum sum is sum of
node 11.

Input:
        1
      /   \
     2     3
    /     /  \
   4     5    6
Output: 16
Explanation: The maximum sum is sum of
nodes 1 4 5 6 , i.e 16. These nodes are
non adjacent.


```
## Approach 
if we take a Root-Node then we dont take its chield but take its grand-child 
```
1.(root.left.left,root.left.right)
2.(root.right.left , root.right.right)
```
if we dont take root-node:
```
then we take chield nodes
root.left
root.right
```

## Solution 1 (Recursive)

```Python
    def getMaxSum(self,root):
        
        if root is None:
            return 0
            
        with_node = root.data
        
        if root.left:
            with_node += self.getMaxSum(root.left.left)
            with_node += self.getMaxSum(root.left.right)
            
        if root.right:
            with_node += self.getMaxSum(root.right.left)
            with_node += self.getMaxSum(root.right.right)
            
        without_node = self.getMaxSum(root.left) + self.getMaxSum(root.right)
            
        ans = max(with_node,without_node)
        
        return ans
```
```bash
Time Complexity : Exponential
Space Complexity : O(n)
```
## Solution (Memoiation)
```
class Solution:
    #Function to return the maximum sum of non-adjacent nodes.
    def getMaxSum(self,root):
        
        return self.solve(root,dict())
        
    def solve(self,root,mapp):
        
        if root is None:
            return 0
        if root in mapp:
            return mapp[root]
            
        with_node = root.data
        
        if root.left:
            with_node += self.solve(root.left.left,mapp)
            with_node += self.solve(root.left.right,mapp)
            
        if root.right:
            with_node += self.solve(root.right.left,mapp)
            with_node += self.solve(root.right.right,mapp)
            
        without_node = self.solve(root.left,mapp) + self.solve(root.right,mapp)
            
        ans = max(with_node,without_node)
        mapp[root] = ans
        
        return mapp[root]
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## GeeksforGeeks

[Maximum sum of Non-adjacent nodes](https://practice.geeksforgeeks.org/problems/maximum-sum-of-non-adjacent-nodes/1?page=1&difficulty[]=1&company[]=Google&category[]=Tree&sortBy=submissions)
