## Number of Distinct Islands
Given a boolean 2D matrix grid of size n * m. You have to find the number of distinct islands where a group of 

connected 1s (horizontally or vertically) forms an island. Two islands are considered to be distinct if and only 

if one island is not equal to another (not rotated or reflected).

## Example 

```bash
Input:
grid[][] = {{1, 1, 0, 0, 0},
            {1, 1, 0, 0, 0},
            {0, 0, 0, 1, 1},
            {0, 0, 0, 1, 1}}
Output:
1
Explanation:
grid[][] = {{1, 1, 0, 0, 0}, 
            {1, 1, 0, 0, 0}, 
            {0, 0, 0, 1, 1}, 
            {0, 0, 0, 1, 1}}
Same colored islands are equal.
We have 2 equal islands, so we 
have only 1 distinct island.

```

## Solution

```python
import sys
from typing import List
sys.setrecursionlimit(10**8)

class Solution:

    def countDistinctIslands(self, grid : List[List[int]]) -> int:
        
        row = len(grid)
        col = len(grid[0])
        shapes = set()
        directions = [(-1,0),(0,1),(1,0),(0,-1)]
        visited=set()
        
        def dfs(x, y, pos, island_direction):
            for dx, dy in directions:
                nx,ny=x+dx,y+dy
                if 0<=nx <row and 0<= ny <col and grid[nx][ny] and (nx,ny) not in visited:
                    temp_direction = (pos[0]+dx, pos[1]+dy)
                    visited.add((nx,ny))
                    island_direction.append(temp_direction)
                    dfs(nx, ny, temp_direction,island_direction)
            return tuple(island_direction)
        
        for x in range(row):
            for y in range(col):
                if grid[x][y] and (x,y) not in visited:
                    visited.add((x,y))
                    shapes.add(dfs(x,y,(0,0),[(0,0)]))
        return len(shapes) 
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Number of Distinct Islands](https://practice.geeksforgeeks.org/problems/number-of-distinct-islands/1)
