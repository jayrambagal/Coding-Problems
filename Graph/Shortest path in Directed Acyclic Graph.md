## Shortest path in Directed Acyclic Graph
Given a Directed Acyclic Graph of N vertices from 0 to N-1 and a 2D Integer array(or vector) edges[ ][ ] 

of length M, where there is a directed edge from edge[i][0] to edge[i][1] with a distance of edge[i][2] for all i, 0<=i

Find the shortest path from src(0) vertex to all the vertices and if it is impossible to reach any vertex, then return -1 for that vertex.

## Example 

```bash
Input:
n = 6, m= 7
edge=[[0,1,2],[0,4,1],[4,5,4]
,[4,2,2],[1,2,3],[2,3,6],[5,3,1]]

Output:
0 2 3 6 1 5
```

## Solution 

```python
class Solution:
    def shortestPath(self, n : int, m : int, edges : List[List[int]]) -> List[int]:
        
        graph = defaultdict(list)
        
        def add(u,v,w):                        #function to create a adj matrix
            graph[u].append((v,w))                
            
        for i in edges:                         # calling function 
            add(i[0],i[1],i[2])
            
            
        def topologicalSortUtil(v,visited,stack):    # topologycal sort using dfs gives the stack

            visited[v] = True

            if v in graph.keys():
                for node,weight in graph[v]:
                    if visited[node] == False:
                        topologicalSortUtil(node,visited,stack)

            stack.append(v)
            
        visited = [False]*(n+1)
        stack = []
        
        for i in range(n):
            if visited[i]==False:
                topologicalSortUtil(i,visited,stack)        #function call for topoligical sort
        
        # main logic
        
        dist = [10000000] * (n)
        dist[0] = 0

        while stack:
            i = stack.pop()

            for node,weight in graph[i]:
                if dist[node] > dist[i] + weight:
                    dist[node] = dist[i] + weight
        
        for i in range(len(dist)):
            if dist[i]==10000000:
                dist[i]=-1
                
        return dist
 ```
#### Complexity
```bash
Time Complexity :O(n) + O(n+m) + O(n) + O(n)
Space Complexity : O(n) + O(n)
```

## Geeksforgeeks
[Shortest path in Directed Acyclic Graph](https://practice.geeksforgeeks.org/problems/shortest-path-in-undirected-graph/1)
