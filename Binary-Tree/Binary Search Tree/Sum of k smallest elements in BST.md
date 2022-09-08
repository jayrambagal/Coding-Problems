## Sum of k smallest elements in BST
 Given a Binary Search Tree. Find sum of all elements smaller than and equal to Kth smallest element.

   
## Example 1


```bash
Input: 
          20
        /    \
       8     22
     /    \
    4     12
         /    \
        10    14   , K=3

Output: 22
Explanation:
Sum of 3 smallest elements are: 
4 + 8 + 10 = 22
```


## Solution 1 

```Python
def summ(root, k):
    st = []
    res = 0
    while True:
        while root:
            st.append(root)
            root = root.left
            
        if not st or not k: 
            return res
            
        node = st.pop()
        k = k-1
        res += node.key
        root = node.right
        
```
```bash
Time Complexity : O(k) 
Space Complexity : O(1) 
```


## GeeksforGeeks

[Sum of k smallest elements in BST](https://practice.geeksforgeeks.org/problems/sum-of-k-smallest-elements-in-bst3029/1)
