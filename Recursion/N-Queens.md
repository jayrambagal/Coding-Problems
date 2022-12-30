## N-Queens
The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other.

Given an integer n, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.

Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space, respectively.

## Example 1
![image](https://user-images.githubusercontent.com/94613732/210059697-89e215f6-25c5-4e46-a4c4-0d0951846a9a.png)


```bash
Input: n = 4
Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above

Input: n = 1
Output: [["Q"]]
```


## Solution 2 (optimization)

```Python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        col = [False]*(n)
        diag1 = [False]*(2*n)
        diag2 = [False]*(2*n)
        ans = []
        def backTrack(y,grid=[]):
            if(y==n):
                ans.append(grid[:])
            else:
                for x in range(0,n):
                    if(col[x] or diag1[x+y] or diag2[x-y+n-1]):continue
                    col[x],diag1[x+y],diag2[x-y+n-1]=1,1,1
                    tempGrid = ['.']*(n)
                    tempGrid[x] = 'Q'
                    grid.append("".join(tempGrid))
                    backTrack(y+1)
                    col[x],diag1[x+y],diag2[x-y+n-1]=0,0,0
                    grid.pop()
        backTrack(0)
        return ans
```
### Complexity
 
```bash
Time Complexity : O(N! * N)
Space Complexity : O(N)
```

## Geeksforgeeks
[N-Queens](https://leetcode.com/problems/n-queens/description/)
