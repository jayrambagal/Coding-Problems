## Sort a 2D vector diagonally
```
Given an NxM 2D matrix, rearrange such that 
Each diagonal in the lower left triangle of the rectangular grid is sorted in ascending order. 
Each diagonal in the upper right triangle of the rectangular grid is sorted in descending order. 
The major diagonal in the grid starting from the top-left corner is not rearranged. 
```
## Example 
```bash
Input:
N = 4, M = 5 
matrix = {{3 6 3 8 2},
          {4 1 9 5 9},
          {5 7 2 4 8},
          {8 3 1 7 6}}
Output:
3 9 8 9 2
1 1 6 5 8
3 4 2 6 3
8 5 7 7 4

```

## Solution
```python
class Solution:
    def diagonalSort(self, mat, m, n):
      # sort diagonaly in asending order
        for i in range(1,m):
          j = i
          k=0
          li =[]
          
          while(j<m and k<n):
            li.append(mat[j][k])
            j+=1
            k+=1
          li.sort();
          
          j=i
          k=0
          l=0
          while(j<m and k<n):
            mat[j][k]=li[l]
            j+=1
            k+=1
            l+=1
        
        # sort diagonaly in desending order
        for i in range(1,n):
          j=0
          k=i
          li =[]
          
          while(j<m and k<n):
            li.append(mat[j][k])
            j+=1
            k+=1
          li.sort();
          h = len(li)
          j=0
          k=i
          l=h-1
          while(j<m and k<n):
            mat[j][k]=li[l]
            j+=1
            k+=1
            l-=1
            
        return mat
```

### Geeksforgeeks
[Sort a 2D vector diagonally](https://practice.geeksforgeeks.org/problems/diagonal-morning-assembly0028/1)

