## Number Of Islands
You are given a n,m which means the row and column of the 2D matrix and an array of  size k denoting the number of operations. Matrix elements is 0 if there is water or 1 if there is land. Originally, the 2D matrix is all 0 which means there is no land in the matrix. The array has k operator(s) and each operator has two integer A[i][0], A[i][1] means that you can change the cell matrix[A[i][0]][A[i][1]] from sea to island. Return how many island are there in the matrix after each operation.You need to return an array of size k.
Note : An island means group of 1s such that they share a common side.
## Example 

```bash
Input: 
Input: n = 4
m = 5
k = 4
A = {{1,1},{0,1},{3,3},{3,4}}

Output: 1 1 2 2

Explanation:
0.  00000
    00000
    00000
    00000
1.  00000
    01000
    00000
    00000
2.  01000
    01000
    00000
    00000
3.  01000
    01000
    00000
    00010
4.  01000
    01000
    00000
    00011

```



## Solution (disjoint set)
```python
from typing import List
class Solution:
    def numOfIslands(self, n: int, m: int, operators : List[List[int]]) -> List[int]:
        
        
        ds = disjoinset(n*m)
        visited = [[0 for i in range(m)] for j in range(n)]
        direction = [(-1,0),(0,-1),(0,1),(1,0)]
        count = 0
        ans = []
        
        def isvalid(i,j,n,m):
            return (0<=i and i<n and j>=0 and j<m)
        
        for i in operators:
            row = i[0]
            col = i[1]
            
            
            if visited[row][col] == 1:
                    ans.append(count)
                    continue
            else:
                visited[row][col] != 1
                count+=1
                visited[row][col] = 1
                
                for i,j in direction:
                    new_row = i+row
                    new_col = j+col
                    
                    if isvalid(new_row,new_col,n,m):
                        if visited[new_row][new_col] ==1:
                            
                            node = row*m + col         #finding the node position
                            new_node = new_row*m + new_col 
                       
                            if ds.find(node) != ds.find(new_node):
                                count-=1
                                ds.union(node,new_node)
                                
                ans.append(count)
            
        return ans
            
        
                    
class desjointset:
    def __init__(self,n):
        
        self.parent = [i for i in range(n)]
        self.rank = [1 for i in range(n)]
        
    def find(self,a):
        
        if self.parent[a]==a:
            return a
            
        self.parent[a] = self.find(self.parent[a])
        return self.parent[a]
        
    def union(self,a,b):
        
        pa = self.find(a)
        pb = self.find(b)
        
        if pa==pb:
            return 
        if self.rank[pa] > self.rank[pb]:
            self.parent[pb] = pa
            self.rank[pa]+= self.rank[pb]
        else:
            self.parent[pa] = pb
            self.rank[pb]+= self.rank[pa]
```
#### Complexity
```bash
Time Complexity : O(V^2) + O(4*alpha)
Space Complexity : O(V)
```
## Geeksforgeeks
[Number Of Islands](https://practice.geeksforgeeks.org/problems/find-the-number-of-islands/1)
