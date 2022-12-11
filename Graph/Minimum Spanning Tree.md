## Minimum Spanning Tree
Given a weighted, undirected and connected graph of V vertices and E edges. The task 

is to find the sum of weights of the edges of the Minimum Spanning Tree.

## Example 

```bash
Input:
3 3
0 1 5
1 2 3
0 2 1
```
![image](https://user-images.githubusercontent.com/94613732/204126158-433e516a-7314-4643-8836-dfe7a708d86e.png)

```
Output:
4
Explanation:
```
![image](https://user-images.githubusercontent.com/94613732/204126164-c3645a7a-4a47-42ea-add1-355d19980269.png)

```

The Spanning Tree resulting in a weight
of 4 is shown above.

```

## Solution (prims algo)

```python
from collections import defaultdict,deque
import heapq
import sys
class Solution:
        
    def spanningTree(self, V, graph):
        
        ans = 0 
        visited = [0]*V
        q = [(0,0)]
        
        while q:
            wt,node = heapq.heappop(q)
            
            if visited[node]==1:
                continue
        
            visited[node] = 1
            ans+=wt
            
            for new_node,new_weight in graph[node]:
                
                if visited[new_node]==0:
                    heapq.heappush(q,(new_weight,new_node))
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(E*logE) + O(E*logE)
Space Complexity : O(E)
```
## Solution (Kruskals algo)

```python
from collections import defaultdict,deque
import heapq
import sys
class Solution:
        
    def spanningTree(self, V, points):
        
        n = len(points)
        edges = []
        
        for i in range(V):
            for j,wt in points[i]:
                edges.append((wt,i,j))
            
        # sort based on cost (i.e. distance)
        edges.sort()
        
        # using Kruskal's algorithm to find the cost of Minimum Spanning Tree
        res = 0
        ds = DisjointSet(n)
        for cost, u, v in edges:
            if ds.find(u) != ds.find(v):
                ds.union(u, v)
                res += cost
        
        return res
        
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
Time Complexity :O(N+E) + O(N*logN) + O(M*4*alpha)   
Space Complexity : O(E)
```
## Geeksforgeeks
[Minimum Spanning Tree](https://practice.geeksforgeeks.org/problems/minimum-spanning-tree/1?page=1&category[]=Graph&sortBy=submissions)
