## Shortest path in Undirected Graph having unit distance
You are given an Undirected Graph having unit weight, Find the shortest path from src(0) to 
all the vertex and if it is unreachable to reach any vertex, then return -1 for that vertex.

## Example 

```bash
Input:
n = 9, m= 10
edges=[[0,1],[0,3],[3,4],[4 ,5]
,[5, 6],[1,2],[2,6],[6,7],[7,8],[6,8]] 
src=0
Output:
0 1 2 1 2 3 3 4 4

```

## Solution (DFS)

```python
class Solution:
    def shortestPath(self, edges, n, m, src):
        
        graph = [[]*m for i in range(n)]
        
        for u,v in edges:
            graph[u].append(v)
            graph[v].append(u)
            
        q = []
        dis = [1e9]*n
        dis[src]=0
        q.append(src)
        
        while q:
            node = q.pop(0)
            
            for i in graph[node]:
                if dis[i]> dis[node]+1:
                    dis[i] = dis[node]+1
                    q.append(i)
        for i in range(len(dis)):
            if dis[i]==1e9:
                dis[i] = -1
        return dis
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```

## Geeksforgeeks
[Shortest path in Undirected Graph having unit distance](https://practice.geeksforgeeks.org/problems/shortest-path-in-undirected-graph-having-unit-distance/1)
