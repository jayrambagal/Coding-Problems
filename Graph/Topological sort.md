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
# Solution (Kahn's Algorithm)

```python
class Solution:

    def topoSort(self, V, adj):
        
        indegree = [0]*V
        
        for i in adj:
            for j in i:
                indegree[j]+=1
                
        q = []
        ans = []
        
        for i in range(V):
            if indegree[i] == 0:
                q.append(i)
        
        while q:
            m = q.pop(0)
            ans.append(m)
            
            for i in adj[m]:
                indegree[i]-=1
                
                if indegree[i]==0:
                    q.append(i)
                    
        return ans
```
#### Complexity
```bash
Time Complexity :O(V+E)
Space Complexity : O(V+E)
```
## Geeksforgeeks
[Topological sort](https://practice.geeksforgeeks.org/problems/topological-sort/1?page=1&difficulty[]=0&difficulty[]=1&category[]=Graph&sortBy=submissions)
