## Count Number of SubTrees having given Sum
Given a binary tree and an integer X. Your task is to complete the function countSubtreesWithSumX() that returns the count 

of the number of subtress having total node’s data sum equal to the value X.

Example: For the tree given below:            

              5
            /    \
        -10     3
        /    \    /  \
      9     8  -4 7

Subtree with sum 7:
             -10
            /      \
          9        8

and one node 7.

   
## Example 1


```bash
Input:
       5
    /    \
  -10     3
 /   \   /  \
 9   8 -4    7
X = 7
Output: 2
Explanation: Subtrees with sum 7 are
[9, 8, -10] and [7] (refer the example
in the problem description).

```


## Solution 1 

```Python
def countSubtreesWithSumX(root, x):
    
    def solve(root,x,count):
        if root is None:
            return 0
        
        summ = solve(root.left,x,count) + root.data + solve(root.right,x,count)
        
        if summ == x:
            count[0]+=1
        return summ
        
    count = [0]
    solve(root,x,count)
    return count[0]

```
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```

## GeeksforGeeks

[Count Number of SubTrees having given Sum](https://practice.geeksforgeeks.org/problems/count-number-of-subtrees-having-given-sum/1?page=1&status[]=unsolved&category[]=Recursion&category[]=Backtracking&sortBy=submissions)
