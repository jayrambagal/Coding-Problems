## Minimum Time to Visit a Cell In a Grid
You are given a m x n matrix grid consisting of non-negative integers where grid[row][col] represents the minimum time required to be able to visit the cell (row, col), which means you can visit the cell (row, col) only when the time you visit it is greater than or equal to grid[row][col].

You are standing in the top-left cell of the matrix in the 0th second, and you must move to any adjacent cell in the four directions: up, down, left, and right. Each move you make takes 1 second.

Return the minimum time required in which you can visit the bottom-right cell of the matrix. If you cannot visit the bottom-right cell, then return -1.
## Example 

![image](https://user-images.githubusercontent.com/94613732/222878230-ee3ba5f6-edb7-433e-86a7-45310bf55ddc.png)

```bash
Input: grid = [[0,1,3,2],[5,1,2,5],[4,3,8,6]]
Output: 7
Explanation: One of the paths that we can take is the following:
- at t = 0, we are on the cell (0,0).
- at t = 1, we move to the cell (0,1). It is possible because grid[0][1] <= 1.
- at t = 2, we move to the cell (1,1). It is possible because grid[1][1] <= 2.
- at t = 3, we move to the cell (1,2). It is possible because grid[1][2] <= 3.
- at t = 4, we move to the cell (1,1). It is possible because grid[1][1] <= 4.
- at t = 5, we move to the cell (1,2). It is possible because grid[1][2] <= 5.
- at t = 6, we move to the cell (1,3). It is possible because grid[1][3] <= 6.
- at t = 7, we move to the cell (2,3). It is possible because grid[1][3] <= 7.
The final time is 7. It can be shown that it is the minimum time possible.

```



## Solution (BFS) heapq
```python
class Solution:
    def minimumTime(self, grid: List[List[int]]) -> int:
        
        n = len(grid)
        m = len(grid[0])       
        directions = [[0,1],[0,-1],[1,0],[-1,0]]
        visited = set()
        heap = [(0,0,0)]
        
        if grid[0][1] >1 and grid[1][0]>1:
            return -1
        
        while heap:
            time,r,c = heappop(heap)
            
            if r==n-1 and c == m-1:
                return time
            
            if (r,c) in visited:
                continue
                
            visited.add((r,c))
            
            for i,j in directions:
                row = i+r
                col = j+c
                
                if (row in range(n)) and (col in range(m)) and ( (row,col) not in visited ):
                
                    if grid[row][col]<= time+1:
                        heappush(heap,(time+1,row,col))
                    else:
                        diff = grid[row][col] - time
                        if diff%2==1:
                            heappush(heap,(grid[row][col],row,col))
                        else:heappush(heap,(grid[row][col]+1,row,col))                  
        return -1
```
#### Complexity
```bash
Time Complexity :  
Space Complexity : 
```
## Geeksforgeeks
[Minimum Time to Visit a Cell In a Grid](https://leetcode.com/problems/minimum-time-to-visit-a-cell-in-a-grid/description/)
