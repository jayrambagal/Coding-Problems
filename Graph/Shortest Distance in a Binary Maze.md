## Shortest Distance in a Binary Maze
Given a n * m matrix grid where each element can either be 0 or 1. You need to find the shortest distance 

between a given source cell to a destination cell. The path can only be created out of a cell if its value is 1. 

If the path is not possible between source cell and destination cell, then return -1.

Note : You can move into an adjacent cell if that adjacent cell is filled with element 1. Two cells are adjacent 

if they share a side. In other words, you can move in one of the four directions, Up, Down, Left and Right.

## Example 

```bash
Input:
grid[][] = {{1, 1, 1, 1},
            {1, 1, 0, 1},
            {1, 1, 1, 1},
            {1, 1, 0, 0},
            {1, 0, 0, 1}}
source = {0, 1}
destination = {2, 2}
Output:
3
Explanation:
1 1 1 1
1 1 0 1
1 1 1 1
1 1 0 0
1 0 0 1
The highlighted part in the matrix denotes the 
shortest path from source to destination cell.

```

## Solution

```python
from typing import List
from collections import deque


class Solution:
    def shortestPath(self, grid: List[List[int]], source: List[int], destination: List[int]) -> int:
        rows = len(grid)
        cols = len(grid[0])
        directions = [[1,0],[-1,0],[0,1],[0,-1]]
        q = deque([])
        q.append((source, 0))
        grid[source[0]][source[1]] = 0 


        
        while q:
            
            (r, c), count = q.popleft()
            
            
            if [r, c] == destination:
                return count
            
            
            for dr, dc in directions:
                row = r+dr
                col = c+dc

                if row not in range(rows) or col not in range(cols) or grid[row][col]==0:
                    continue

                grid[row][col] = 0
                q.append(((row, col), count + 1))

        return -1
 ```
#### Complexity
```bash
Time Complexity : 
Space Complexity : 
```
## Geeksforgeeks
[Shortest Distance in a Binary Maze](https://practice.geeksforgeeks.org/problems/shortest-path-in-a-binary-maze-1655453161/1)
