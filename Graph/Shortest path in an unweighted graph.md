## Shortest path in an unweighted graph
The city of Ninjaland is analogous to the unweighted graph. The city has 'N' houses numbered from 1 to N
respectively and are connected by M bidirectional roads. If a road is connecting two houses 'X and 'Y which
means you can go from X to '"Y or "Y to X. It is guaranteed that you can reach any house from any other
house via some combination of roads. Two houses are directly connected by at max one road.
A path between house 'S' to house T is defined as a sequence of vertices from 'S' to T. Where starting
house is 'S' and the ending house is T and there is a road connecting two consecutive houses. Basically, the
path looks like this: (S,h1,h2,h3,. T). you have to find the shortest path from 'S' to T.

## Example 

```bash

```
![image](https://user-images.githubusercontent.com/94613732/204073707-b5f3dddf-1d28-445e-b156-8dafaed18669.png)


```bash
Output : [1,3,8]

```

## Solution (DFS)

```python
def shortestPath(edges, n, m, s, t):
    graph = [[] for i in range(n+1)]
    
    for i in range(len(edges)):
        graph[edges[i][0]].append(edges[i][1])
        graph[edges[i][1]].append(edges[i][0])
        
    visited = [False]*(n+1)
    parent = [-1]*(n+1)
    q = [s]
    visited[s]=True
    parent[s] = -1
    
    while q:
        m = q.pop(0)
        for x in graph[m]:
            if visited[x]==False:
                q.append(x)
                visited[x]=True
                parent[x] = m
    
    curr = t
    ans = [t]
    while curr!=s:
        curr = parent[curr]
        ans.append(curr)
        
    return ans[::-1]
        
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Geeksforgeeks
[Shortest path in an unweighted graph](https://www.codingninjas.com/codestudio/problems/shortest-path-in-an-unweighted-graph_981297?leftPanelTab=0)
