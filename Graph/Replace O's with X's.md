## Replace O's with X's
Given a matrix mat of size N x M where every element is either ‘O’ or ‘X’. Replace all ‘O’ with ‘X’ that are surrounded by ‘X’.

A ‘O’ (or a set of ‘O’) is considered to be by surrounded by ‘X’ if there are ‘X’ at locations just below, just above, just left and just right of it.

## Example 

```bash
Input: n = 5, m = 4
mat = {{'X', 'X', 'X', 'X'}, 
       {'X', 'O', 'X', 'X'}, 
       {'X', 'O', 'O', 'X'}, 
       {'X', 'O', 'X', 'X'}, 
       {'X', 'X', 'O', 'O'}}
Output: ans = {{'X', 'X', 'X', 'X'}, 
               {'X', 'X', 'X', 'X'}, 
               {'X', 'X', 'X', 'X'}, 
               {'X', 'X', 'X', 'X'}, 
               {'X', 'X', 'O', 'O'}}
Explanation: Following the rule the above 
matrix is the resultant matrix.

```

## Solution

```python
from collections import deque
class Solution:
    def fill(self, m, n, board):
        
        visited = [[False]*n for _ in range(m)]
        queue = deque([])
        
        
        for i in range(m):
            if board[i][0] == "O":
                queue.append((i, 0))
                visited[i][0] = True
            if board[i][n-1] == "O":
                queue.append((i, n-1))
                visited[i][n-1] = True
        for i in range(n):
            if board[0][i] == "O":
                queue.append((0, i))
                visited[0][i] = True
            if board[m-1][i] == "O":
                queue.append((m-1, i))
                visited[m-1][i] = True
        
        
        connections = [(-1, 0), (1, 0), (0, -1), (0, 1)]
        while queue:
            cur_i, cur_j = queue.popleft()
            for d_i, d_j in connections:
                new_i, new_j = cur_i+d_i, cur_j+d_j
                if 0 <= new_i < m and 0 <= new_j < n and board[new_i][new_j] == "O" and not visited[new_i][new_j]:
                    visited[new_i][new_j] = True
                    queue.append((new_i, new_j))
        
        
        for i in range(1, m-1):
            for j in range(1, n-1):
                if board[i][j] == "O" and not visited[i][j]:
                    board[i][j] = "X"
	    return board 
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Replace O's with X's](https://practice.geeksforgeeks.org/problems/replace-os-with-xs0052/1)
