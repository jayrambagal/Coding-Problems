## Maximum Rectangular Area in a Histogram

Find the largest rectangular area possible in a given histogram where the largest rectangle can be made 

of a number of contiguous bars. For simplicity, assume that all bars have the same width and the width is 

1 unit, there will be N bars height of each bar will be given by the array arr.

#### Example
```bash
Input:
N = 7
arr[] = {6,2,5,4,5,1,6}
Output: 12

```
### Solution 

```python
class Solution:

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
Time Complexity = O(n)
Space Complexity = O(n) 
```


## Geeksforgeeks    
[Maximum Rectangular Area in a Histogram](https://practice.geeksforgeeks.org/problems/maximum-rectangular-area-in-a-histogram-1587115620/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Stack&category[]=Queue&category[]=two-pointer-algorithm&category[]=sliding-window&sortBy=submissions)
