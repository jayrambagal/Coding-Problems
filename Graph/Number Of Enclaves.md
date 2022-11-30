## Number Of Enclaves
You are given an n x m binary matrix grid, where 0 represents a sea cell and 1 represents a land cell.

A move consists of walking from one land cell to another adjacent (4-directionally) land cell or walking off the boundary of the grid.

Find the number of land cells in grid for which we cannot walk off the boundary of the grid in any number of moves.

## Example 

```bash
Input:
grid[][] = {{0, 0, 0, 0},
            {1, 0, 1, 0},
            {0, 1, 1, 0},
            {0, 0, 0, 0}}
Output:
3
Explanation:
0 0 0 0
1 0 1 0
0 1 1 0
0 0 0 0
The highlighted cells represents the land cells.
```

## Solution

```python
from collections import deque
from typing import List

class Solution:    
    def numberOfEnclaves(self, grid: List[List[int]]) -> int:
        
        n = len(grid)
        m = len(grid[0])
        visited=[[0]*m for i in range(n)]
        q = deque([])
        
        for i in range(n):
            if grid[i][0] == 1:
                q.append((i, 0))
                visited[i][0] = 1
                
            if grid[i][m-1] == 1:
                q.append((i, m-1))
                visited[i][m-1] = 1
                
        for i in range(m):
            if grid[0][i] == 1:
                q.append((0, i))
                visited[0][i] = 1
            if grid[n-1][i] == 1:
                q.append((n-1, i))
                visited[n-1][i] = 1
                
        connections = [(-1, 0), (1, 0), (0, -1), (0, 1)]
        while q:
            cur_i, cur_j = q.popleft()
            
            for d_i, d_j in connections:
                new_i, new_j = cur_i+d_i, cur_j+d_j
                if 0 <= new_i < n and 0 <= new_j < m and grid[new_i][new_j] == 1 and visited[new_i][new_j]==0:
                    visited[new_i][new_j] = 1
                    q.append((new_i, new_j)) 
        ans = 0            
        for i in range(n):
            for j in range(m):
                if grid[i][j]==1 and visited[i][j]==0:
                    ans+=1
        return ans
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Number Of Enclaves](https://practice.geeksforgeeks.org/problems/number-of-enclaves/1)
