## Connecting the graph
You are given a graph with n vertices and m edges.

You can remove one edge from anywhere and add that edge between any two vertices in one operation.

Find the minimum number of operation that will be required to make the graph connected.

If it is not possible to make the graph connected, return -1.
## Example 

```bash
n=4
m=3
Edge=[ [0, 1] , [0, 2] , [1, 2] ]

Output:
1

Explanation:
Remove edge between vertices 1 and 2 and add between vertices 1 and 3.


Input:
n=6
m=5
Edge=[ [0,1] , [0,2] , [0,3] , [1,2] , [1,3] ]

Output:
2

Explanation:
Remove edge between (1,2) and(0,3) and add edge between (1,4) and (3,5)
```
## Aproach
```
given a disconnected graph  we can connetct the graph using extra edges using in connected graph 
using disjoin set we can easily find the extra edges. 
and also find the disconnected graph count.
```
## Solution

```python
class Solution:
    def Solve(self, n, adj):
        
        count_extra = 0
        ds = DisjointSet(n)
        for i, j in adj:
            
            if ds.find(i) == ds.find(j):
                count_extra+=1
            else:
                ds.union(i,j)
                
        count_parent = 0
        for i in range(n):
            if i == ds.parent[i]:
                count_parent+=1
                
        
        if count_extra >= count_parent-1:
            return count_parent-1
        else:
            return -1
        
        
class DisjointSet:
    def __init__(self, n):
        self.parent = [i for i in range(n)]
        self.rank = [1 for _ in range(n)]
    
    # make a and b part of the same component
    # union by rank optimization
    def union(self, a, b):
        pa = self.find(a)
        pb = self.find(b)
        if pa == pb: return
        if self.rank[pa] > self.rank[pb]:
            self.parent[pb] = pa
            self.rank[pa] += self.rank[pb]
        else:
            self.parent[pa] = pb
            self.rank[pb] += self.rank[pa]
    
    # find the representative of the 
    # path compression optimization
    def find(self, a):
        if self.parent[a] == a:
            return a
        
        self.parent[a] = self.find(self.parent[a])
        return self.parent[a]
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Connecting the graph](https://practice.geeksforgeeks.org/problems/connecting-the-graph/1?page=1&sortBy=accuracy&query=page1sortByaccuracy)
