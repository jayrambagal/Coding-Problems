## Rotten Oranges
Given a grid of dimension nxm where each cell in the grid can have values 0, 1 or 2 which has the following meaning:
0 : Empty cell
1 : Cells have fresh oranges
2 : Cells have rotten oranges

We have to determine what is the minimum time required to rot all oranges. A rotten orange at index [i,j] 

can rot other fresh orange at indexes [i-1,j], [i+1,j], [i,j-1], [i,j+1] (up, down, left and right) in unit time. 

## Example 

```bash
Input: grid = {{0,1,2},{0,1,2},{2,1,1}}
Output: 1
Explanation: The grid is-
0 1 2
0 1 2
2 1 1
Oranges at positions (0,2), (1,2), (2,0)
will rot oranges at (0,1), (1,1), (2,2) and 
(2,1) in unit time.
```

## Solution

```python
class Solution:

    #Function to find minimum time required to rot all oranges. 
	def orangesRotting(self, grid):
		q = []
		ans = 0
		
		for i in range(len(grid)):
		    for j in range(len(grid[0])):
		        if grid[i][j]==2:
		            q.append((i,j,0))
		        elif grid[i][j]==1:
		            ans+=1
		
		while q:
		    i,j,unit = q.pop(0)
		    
		    row = [-1,0,1,0]
		    col = [+0,1,0,-1]
		    
		    for k in range(4):
		        n_row = i+row[k]
		        n_col = j+col[k]
		        
		        if n_row in range(len(grid)) and n_col in range(len(grid[0])) and grid[n_row][n_col]==1:
		            grid[n_row][n_col] = 2
		            ans-=1
		            q.append((n_row,n_col,unit+1))
	    
	    if ans==0:        	    
		    return unit
		else:
		    return -1
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Rotten Oranges](https://practice.geeksforgeeks.org/problems/rotten-oranges2536/1)
