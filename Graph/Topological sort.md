## Topological sort
Given a Directed Acyclic Graph (DAG) with V vertices and E edges, Find any Topological Sorting of that Graph.

## Example 

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/203973809-dcdf8ea7-ed09-485d-9161-e5942e11f99f.png)
```bash
Output : 1

```

## Solution 

```python
class Solution:

    def topoSort(self, V, adj):
        
        visited = [False]*V
        stack = []
        
        def topo(adj,visited,stack,node):
            visited[node] = True
            for i in adj[node]:
                if visited[i]==False:
                    topo(adj,visited,stack,i)
                    
            stack.append(node)
            
            
        for i in range(V):
            if visited[i]==False:
                topo(adj,visited,stack,i)
                
        return stack[::-1]
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Geeksforgeeks
[Topological sort](https://practice.geeksforgeeks.org/problems/topological-sort/1?page=1&difficulty[]=0&difficulty[]=1&category[]=Graph&sortBy=submissions)
