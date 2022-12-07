## Path With Minimum Effort
You are a hiker preparing for an upcoming hike. You are given heights, a 2D array of size rows x columns, 
where heights[row][col] represents the height of cell (row, col). You are situated in the top-left cell, (0, 0), 
and you hope to travel to the bottom-right cell, (rows-1, columns-1) (i.e., 0-indexed). You can move up, down, left, or right, 
and you wish to find a route that requires the minimum effort.

A route's effort is the maximum absolute difference in heights between two consecutive cells of the route.
## Example 

```bash
heights = [[1,2,2],[3,8,2],[5,3,5]]
Output: 2
Explaination: The route of [1,3,5,3,5] has a maximum absolute difference of 2 in consecutive cells.
This is better than the route of [1,2,2,2,5], where the maximum absolute difference is 3.
```

## Solution

```python
import heapq 
class Solution:
        
    def MinimumEffort(self, heights):
        
        m, n = len(heights), len(heights[0])
        pq = [(0, 0, 0)] # diff, i, j
        # effort is the distance from source
        effort = {(i, j): float('inf') for i in range(m) for j in range(n)}
        effort[0, 0] = 0
        while pq:
            diff, i, j = heapq.heappop(pq)
            for ni, nj in self.get_next(heights, i, j):
                new_diff = max(diff, abs(heights[i][j]-heights[ni][nj]))
                if effort[ni, nj] > new_diff:
                    effort[ni, nj] = new_diff 
                    heapq.heappush(pq, (new_diff, ni, nj))
        return effort[m-1, n-1]
        
    def get_next(self, A, i, j):
        coords = []
        for di, dj in [[0,1], [0,-1],[1,0],[-1,0]]:
            ni, nj = di+i, dj+j
            if 0 <= ni < len(A) and 0 <= nj < len(A[0]):
                coords.append((ni, nj))
        return coords
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Path With Minimum Effort](https://practice.geeksforgeeks.org/problems/path-with-minimum-effort/1)
