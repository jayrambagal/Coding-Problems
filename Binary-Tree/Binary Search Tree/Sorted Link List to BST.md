## Sorted Link List to BST
Given a Singly Linked List which has data members sorted in ascending order. 

Construct a Balanced Binary Search Tree which has same data members as the given Linked List.

Note: There might be nodes with the same value.

   
## Example 1


```bash
Input:
Linked List: 1->2->3->4->5->6->7
Output:
4 2 1 3 6 5 7
Explanation :
The BST formed using elements of the 
linked list is,
        4
      /   \
     2     6
   /  \   / \
  1   3  5   7  
Hence, preorder traversal of this 
tree is 4 2 1 3 6 5 7
```


## Solution 1 

```Python
class Solution:
    def sortedListToBST(self, head):
        arr = []
        while head:
            arr.append(head.data)
            head = head.next
            
        n = len(arr)
        
        start = 0
        end = n-1
        
        return self.solve(arr,start,end)
        
    def solve(self,arr,s,e):
        if s>e:
            return None
        mid = int(s +1+ e)//2
        
        temp = TNode(arr[mid])
        
            
        temp.left = self.solve(arr,s,mid-1)
        temp.right = self.solve(arr,mid+1,e)
        
        return temp
```
```bash
Time Complexity : O(n) 
Space Complexity : O(n) + O(n)
```
## Solution

```python
class Solution:

   def sortedListToBST(self, head):
       
       l=[]
       while head:
           l.append(head.data)
           head=head.next
       return self.arraytotree(l)

   def arraytotree(self,A):
       if not A:
           return 
       n=len(A)
       p=n//2
       root=TNode(A[p])
       root.left=self.arraytotree(A[:p])
       root.right=self.arraytotree(A[p+1:])
       return root
```


## GeeksforGeeks

[Sorted Link List to BST](https://practice.geeksforgeeks.org/problems/sorted-list-to-bst/1?page=1&difficulty[]=1&difficulty[]=2&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Binary%20Search%20Tree&sortBy=submissions)
