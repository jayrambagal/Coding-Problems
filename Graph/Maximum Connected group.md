## Maximum Connected group
You are given an n x n binary grid. A grid is said to be binary if every value in grid is either 1 or 0.

You can change at most one cell in grid from 0 to 1.

You need to find the largest group of connected  1's.

Two cells are said to be connected if both are adjacent to each other and both have same value.
## Example 

```bash
Input:
2
1 1
0 1

Output:
4

Explanation:
By changing cell (2,1) ,we can obtain a connected group of 4 1's
1 1
1 1
 

Example 2

Input:
3
1 0 1
1 0 1
1 0 1

Output:
7

Explanation:
By changing cell (3,2) ,we can obtain a connected group of 7 1's
1 0 1
1 0 1
1 1 1
```

## Solution

```python
from typing import List
class Solution:
    def MaxConnection(self, grid : List[List[int]]) -> int:
        
         n = len(grid)
         m = len(grid[0])
         ds = disjoinset(n*n)
         direction = [(-1,0),(0,-1),(1,0),(0,1)]
         mx = 0
         count = 0
         
         def isvalid(i,j,n):
             return (0<=i and i<n and 0<=j and j<n)
         
         for i in range(n):
             for j in range(n):
                 if grid[i][j]==1:
                     for row,col in direction:
                         new_row = row+i
                         new_col = col+j
                         
                         if isvalid(new_row,new_col,n):
                             if grid[new_row][new_col] == 1:
                                 node = i*n+j # claculating the node size 
                                 new_node =new_row*n+new_col
                                 
                                 ds.union(node,new_node)
                 else:
                     count+=1
                     
         if count == 0:    #means grid contains all 1's so we return grid size
             return n*n  
                                
         for k in range(n):
             for l in range(m):
                 if grid[k][l]==0:
                     s = set()  
                     for row,col in direction:
                         new_row = row+k
                         new_col = col+l
                         
                         if isvalid(new_row,new_col,n):
                             if grid[new_row][new_col] == 1:
                                 
                                 s.add(ds.find(new_row*n+new_col))
                     totalsize = 0
                     for i in s:
                         totalsize += ds.rank[i]
                     mx = max(mx,totalsize)
         return mx+1
                         
        
        
class disjoinset:
    def __init__(self,n):
        self.parent = [i for i in range(n)]
        self.rank = [1 for i in range(n)]
        
    def find(self,a):
        if self.parent[a] == a:
            return a
        self.parent[a] = self.find(self.parent[a])
        
        return self.parent[a]
    
    def union(self,a,b):
        
        pa = self.find(a)
        pb = self.find(b)
        
        if pa == pb:
            return 
        
        if self.rank[pa]>self.rank[pb]:
            self.parent[pb] = pa
            self.rank[pa]+=self.rank[pb]
        else:
            self.parent[pa] = pb
            self.rank[pb]+=self.rank[pa]
            
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Maximum Connected group](https://practice.geeksforgeeks.org/problems/maximum-connected-group/1)
