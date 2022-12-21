## Knight Walk
Given a square chessboard, the initial position of Knight and position of a target. 

Find out the minimum steps a Knight will take to reach the target position.If it cannot reach the target position return -1.

Note:

The initial and the target position co-ordinates of Knight have been given accoring to 1-base indexing.
## Example 

```bash
Input:
N=8
knightPos[ ] = {7, 7}
targetPos[ ] = {1, 5}
Output:
4
Explanation:
Knight takes 4 steps to reach from
(7, 7) to (1, 5):
(4, 5) -> (6, 5) -> (5, 3) -> (7, 2) -> (1, 5).
```

## Solution

```python
class Solution:
    
	def minStepToReachTarget(self, KnightPos, TargetPos, N):
	    
        moves = [[-2,-1], [-2,1], [-1,-2], [1,-2], [-1,2], [1,2], [2,-1], [2,1]]
        seen = set()
        seen.add((KnightPos[0]-1, KnightPos[1]-1))
        q = [(KnightPos[0]-1, KnightPos[1]-1, 0)]
        
        while q:
            
            i, j, min_steps = q.pop(0)
            
            if i == TargetPos[0]-1 and j == TargetPos[1]-1:
                return min_steps
                
            for move in moves:
                x = move[0] + i
                y = move[1] + j
                
                if 0 <= x < N and 0 <= y < N and (x, y) not in seen:
                    q.append((x, y, min_steps + 1))
                    seen.add((x, y))
                    
        return -1
 ```
#### Complexity
```bash
Time Complexity :O(n*n)
Space Complexity :O(n*n) 
```
## Geeksforgeeks
[Knight Walk](https://practice.geeksforgeeks.org/problems/knight-walk4521/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Graph&sortBy=submissions)
