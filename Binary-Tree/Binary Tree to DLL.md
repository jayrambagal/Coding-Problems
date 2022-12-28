## Binary Tree to DLL
```
Given a Binary Tree (BT), convert it to a Doubly Linked List(DLL) In-Place. 
The left and right pointers in nodes are to be used as previous and next 
pointers respectively in converted DLL. The order of nodes in DLL must be 
same as Inorder of the given Binary Tree. The first node of Inorder traversal 
(leftmost node in BT) must be the head node of the DLL.
```
   
## Example 1


```bash
Input:
      1
    /  \
   3    2
Output:
3 1 2 
2 1 3 
Explanation: DLL would be 3<=>1<=>2

```


## Solution 1 

```Python
class Solution:
    def bToDLL(self, root):
        head, prev = None, None
        
        def convert(n):
            nonlocal head, prev
            if not n:
                return
            
            convert(n.left)
            if not head:
                head = n
            if prev:
                prev.right = n
                n.left = prev
            prev = n
            convert(n.right)
            
        convert(root)
        return head
```

```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Binary Tree to DLL](https://practice.geeksforgeeks.org/problems/binary-tree-to-dll/1)
