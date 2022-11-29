## Distance of nearest cell having 1
Given a binary grid of n*m. Find the distance of the nearest 1 in the grid for each cell.

The distance is calculated as |i1  - i2| + |j1 - j2|, where i1, j1 are the row number and 

column number of the current cell, and i2, j2 are the row number and column number of the nearest cell having value 1.
## Example 

```bash
Input: grid = {{0,1,1,0},{1,1,0,0},{0,0,1,1}}
Output: {{1,0,0,1},{0,0,1,1},{1,1,0,0}}
Explanation: The grid is-
0 1 1 0 
1 1 0 0 
0 0 1 1 
0's at (0,0), (0,3), (1,2), (1,3), (2,0) and
(2,1) are at a distance of 1 from 1's at (0,1),
(0,2), (0,2), (2,3), (1,0) and (1,1)
respectively.
```
![image](https://user-images.githubusercontent.com/94613732/204526915-3022c75b-a893-49c3-b182-16820e56ad9d.png)

## Solution

```python
from collections import deque
class Solution:

    #Function to find distance of nearest 1 in the grid for each cell.
	def nearest(self, grid):
		#Code here
		
		q = deque([])
		rows = len(grid)
		cols = len(grid[0])
		distance = [["."]*cols for i in range(rows)]
		visited = set()
		directions = [[1,0],[-1,0],[0,1],[0,-1]]
		
		for i in range(rows):
		    for j in range(cols):
		        if grid[i][j]==1:
		            visited.add((i,j))
		            q.append(((i,j),0))
		            distance[i][j]=0
		
		while q:
		    (r,c),step = q.popleft()
		    
		    for dr,dc in directions:
		        row = r+dr
		        col = c+dc
		        
		        if row not in range(rows) or col not in range(cols) or (row,col) in visited or grid[row][col]==1:
		            continue
		        
		        
		        distance[row][col] = step+1
		        visited.add((row,col))
		        q.append(((row,col),step+1))
		return distance
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Distance of nearest cell having 1](https://practice.geeksforgeeks.org/problems/distance-of-nearest-cell-having-1-1587115620/1)
