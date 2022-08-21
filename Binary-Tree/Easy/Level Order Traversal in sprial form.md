## Level order traversal in spiral form
Complete the function to find spiral order traversal of a tree. For below tree, function should return 1, 2, 3, 4, 5, 6, 7.
  
## Example 1


```bash
Input:
      1
    /   \
   3     2
Output:1 3 2

Input:
           10
         /     \
        20     30
      /    \
    40     60
Output: 10 20 30 60 40 

```

## Solution 1 

```Python
def findSpiral(root):
    
        if root == None:
            return []
    
        ans = []
        stack = [root]
        direction =1
        
        while stack: 
            level = []
            for i in range(len(stack)):
                node = stack.pop(0)
                level.append(node.data)
                
                
                if node.left !=None: 
                    stack.append(node.left)
                if node.right !=None:
                    stack.append(node.right)
                    
            if direction %2==0:
                ans.append(level)
            else:
                ans.append(level[::-1])
                
            direction+=1
            
        res = []
        for i in ans:
            for j in i:
                res.append(j)

        return res
        
```
```bash
Time Complexity : O(n)
Space Complexity : O(n) + O(n)
```
## GeeksforGeeks

[Level order traversal in spiral form](https://practice.geeksforgeeks.org/problems/level-order-traversal-in-spiral-form/1?page=1&difficulty[]=0&category[]=Tree&sortBy=submissions)
