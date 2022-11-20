## Max rectangle

Given a binary matrix M of size n X m. Find the maximum area of a rectangle formed only of 1s in the given matrix.

#### Example
```bash
Input:
n = 4, m = 4
M[][] = {{0 1 1 0},
         {1 1 1 1},
         {1 1 1 1},
         {1 1 0 0}}
Output: 8
Explanation: For the above test case the
matrix will look like
0 1 1 0
1 1 1 1
1 1 1 1
1 1 0 0
the max size rectangle is 
1 1 1 1
1 1 1 1
and area is 4 *2 = 8.

```
### Solution 

```python
class Solution:

class Solution:
    def maxArea(self,M, n, m):
        area = self.getMaxArea(M[0])
        
        for i in range(1,n):
            for j in range(m):
                if M[i][j]!=0:
                    M[i][j] = M[i][j] + M[i-1][j]
                else:
                    M[i][j] = 0
            area = max(area,self.getMaxArea(M[i]))
            
        return area
    def getMaxArea(self,histogram):
        
        stack = list()
        max_area = 0  
        index = 0
  
        while index < len(histogram):

      
            if (not stack) or (histogram[stack[-1]] <= histogram[index]):
                stack.append(index)
                index += 1

            else:
                top_of_stack = stack.pop()

                area = (histogram[top_of_stack] *
                        ((index - stack[-1] - 1)
                         if stack else index))

                max_area = max(max_area, area)

        while stack:
      
            top_of_stack = stack.pop()
            
    
            area = (histogram[top_of_stack] *
                    ((index - stack[-1] - 1)
                     if stack else index))
                     
            max_area = max(max_area, area)
     
        return max_area

        
```
### Complexity
```bash
Time Complexity = O(n*m) 
Space Complexity = O(m) 
```


## Geeksforgeeks    
[Max rectangle](https://practice.geeksforgeeks.org/problems/max-rectangle/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Stack&category[]=Queue&category[]=two-pointer-algorithm&category[]=sliding-window&sortBy=submissions)
