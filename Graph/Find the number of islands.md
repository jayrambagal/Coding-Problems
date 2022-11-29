## Find the number of islands
Given a grid of size n*m (n is the number of rows and m is the number of columns in the grid) 

consisting of '0's (Water) and '1's(Land). Find the number of islands.

Note: An island is surrounded by water and is formed by connecting adjacent lands 

horizontally or vertically or diagonally i.e., in all 8 directions.

## Example 

```bash
Input:
grid = {{0,1},{1,0},{1,1},{1,0}}
Output:
1
Explanation:
The grid is-
0 1
1 0
1 1
1 0
All lands are connected.

Input:
grid = {{0,1,1,1,0,0,0},{0,0,1,1,0,1,0}}
Output:
2
Expanation:
The grid is-
0 1 1 1 0 0 0
0 0 1 1 0 1 0 
There are two islands :- one is colored in blue 
and other in orange.

```

## Solution

```python
import sys
from collections import deque
sys.setrecursionlimit(10**8)
class Solution:
    
    def numIslands(self,grid):
        n = len(grid)
        m = len(grid[0])
        
        def bfs(row,col,grid):
            q=deque()
            q.append((row,col))
            grid[row][col]=0
            
            while q:
                row,col=q.popleft()
                X = [0, 1,  0, -1,  -1,  1, -1,  1]
                Y = [1, 0, -1,  0,  -1,  1,  1, -1]
                for i,j in zip(X,Y):
                    n_row = row + i
                    n_cow = col + j
                    if n_row in range(n) and n_cow in range(m) and (n_row,n_cow) and grid[n_row][n_cow]==1:
                        q.append((n_row,n_cow))
                        grid[n_row][n_cow]=0

        islands=0
        for i in range(n):
            for j in range(m):
                if grid[i][j]==1:
                    islands+=1
                    bfs(i,j,grid)
        return islands
 ```
#### Complexity
```bash
Time Complexity : O(8 * n^2)
Space Complexity : O(n^2)
```
## Geeksforgeeks
[Find the number of islands](https://practice.geeksforgeeks.org/problems/find-the-number-of-islands/1?page=1&category[]=Graph&sortBy=submissions)
