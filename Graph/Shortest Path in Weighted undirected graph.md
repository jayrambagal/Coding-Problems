## Shortest Path in Weighted undirected graph
```
You are given a weighted undirected graph having n+1 vertices numbered from 0 to n and m edges 
describing there are edges between a to b with some weight, find the shortest path between the 
vertex 1 and the vertex n and if path does not exist then return a list consisting of only -1.
```
## Example 

```bash
Example:
Input:
n = 5, m= 6
edges = [[1,2,2], [2,5,5], [2,3,4], [1,4,1],[4,3,3],[3,5,1]]
Output:
1 4 3 5
Explaination:
Shortest path from 1 to n is by the path 1 4 3 5
```

## Solution
```python
from collections import deque
from collections import defaultdict
class Solution:
    def shortestPath(self, n, m, edges):
        
        adj = defaultdict(list)
        def add(u,v,wt):
            adj[u].append([v,wt])
            adj[v].append([u,wt])
            
        for i in edges:
            add(i[0],i[1],i[2])
        
        parent = [-1 for i in range(n+1)]
        dis = [9999999]*(n+1)
        dis [1] = 0
        q = deque([])
        q.append((1,0))
        
        while q:
            node,node_dis = q.popleft()
            
            for i,wt in adj[node]:
                if wt + dis[node] < dis[i]:
                    dis[i] = wt+dis[node]
                    parent[i] = node
                    q.append((i,dis[i]))
        
        if dis[n]==9999999:
            return [-1]
        ans = []
        while n>0:
            ans.append(n)
            n = parent[n]
            
        return ans[::-1]
            
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Shortest Path in Weighted undirected graph](https://practice.geeksforgeeks.org/problems/shortest-path-in-weighted-undirected-graph/1)
