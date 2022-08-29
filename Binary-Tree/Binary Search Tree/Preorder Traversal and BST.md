## Preorder Traversal and BST
Given an array arr[ ] of size N consisting of distinct integers, write a program that

returns 1 if given array can represent preorder traversal of a possible BST, else returns 0.

   
## Example 1


```bash
Input:
N = 3
arr = {2, 4, 3}
Output: 1
Explaination: Given arr[] can represent
preorder traversal of following BST:
               2
                \
                 4
                /
               3

```


## Solution 1 (Brut Force)

```Python
class Solution:
    def canRepresentBST(self, arr, N):
        
        for i in range(N):
            for j in range(i+1,N):
                if  arr[j]> arr[i]:
                    for k in range(j+1,N):
                        if arr[i]>arr[k]:
                            return 0
                            
        return 1
```
```bash
Time Complexity : O(n^2)
Space Complexity : O(1)
```

## Solution (stack)
```python
class Solution:
    def canRepresentBST(self, arr, N):
        
        stack = []
        root = -1e9
        
        for i in range(N):
            if arr[i]< root:
                return 0
                
            while stack and arr[i]>stack[-1]:
                root = stack[-1]
                stack.pop()
                
            stack.append(arr[i])
            
        return 1
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Preorder Traversal and BST](https://practice.geeksforgeeks.org/problems/preorder-traversal-and-bst4006/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
