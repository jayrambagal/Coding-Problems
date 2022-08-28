## Sort the Matrix Diagonally
```
A matrix diagonal is a diagonal line of cells starting from some cell in either the topmost 
row or leftmost column and going in the bottom-right direction until reaching the matrix's end. 
For example, the matrix diagonal starting from mat[2][0], where mat is a 6 x 3 matrix, includes cells mat[2][0], mat[3][1], and mat[4][2].

Given an m x n matrix mat of integers, sort each matrix diagonal in ascending order and return the resulting matrix.
```
## Example 
```bash
Input: mat = [[3,3,1,1],[2,2,1,2],[1,1,1,2]]
Output: [[1,1,1,1],[1,2,2,2],[1,2,3,3]]


```
## Solution

```python

class Solution:
    def diagonalSort(self, mat: List[List[int]]) -> List[List[int]]:
        num_cols = len(mat[0])
        num_rows = len(mat)
        unsorted = True
        
        while unsorted:
            unsorted = False
            for row in range(num_rows - 1):
                for col in range(num_cols - 1):
                    if mat[row][col] > mat[row+1][col+1]:
                        unsorted = True
                        mat[row][col], mat[row+1][col+1] = mat[row+1][col+1], mat[row][col]
        
        return mat
```

### Leetcode
[Sort the Matrix Diagonally](https://leetcode.com/problems/sort-the-matrix-diagonally/)


