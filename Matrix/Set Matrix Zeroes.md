##  Set Matrix Zeroes
Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.

## Example 
```bash

Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]
Output: [[1,0,1],[0,0,0],[1,0,1]]


```
## Solution

```python

class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        n = len(matrix)
        m = len(matrix[0])
        make_zeros = []
        for i in range(n):
            for j in range(m):
                if matrix[i][j] == 0:
                    make_zeros.append(i)
                    make_zeros.append(j)

        for i in range(0,len(make_zeros)-1,2):
            k = 0
            l = make_zeros[i+1]
            while k<n:
                matrix[k][l] = 0
                k+=1

            x = make_zeros[i]
            y = 0

            while y< m:
                matrix[x][y]=0
                y+=1

        return matrix
```
## Complexity
```
Time Complexity : O(n*m) + O(len(make_zeros)*n+m)
Space Complexity : O(k)
```


## Geeksforgeeks
[ Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description/)
