## Strongly Connected Components (Kosaraju's Algo)
Given a Directed Graph with V vertices (Numbered from 0 to V-1) and E edges, Find the number of strongly connected components in the graph.
## Example 

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/207393257-7ab1956e-96fe-42e5-b691-87906b8ecb87.png)
```
Output:
3
Explanation:
```
![image](https://user-images.githubusercontent.com/94613732/207393366-bd9e635f-b4da-4a86-ac6b-959c51934cd4.png)
```

We can clearly see that there are 3 Strongly
Connected Components in the Graph
```

## Solution

```python
class Solution:

    def kosaraju(self, V, adj):

        vis= [0 for i in range(V)]
        stack=[]
        for i in range(V):
            if vis[i]==0:
                self.dfs(vis,adj,i,stack)
                
        
        transpose = [[] for i in range(V)]
        for i in range(V):
            for j in adj[i]:
                transpose[j].append(i)
                
        count=0        
        visited = [0 for i in range(V)]
        for i in range(V):
            val = stack.pop()
            
            if visited[val]==0:
                count+=1
                self.dfsnew(val,visited,transpose)
        return count

    
    def dfs(self,vis,adj,node,stack):
        vis[node]=1
        for i in adj[node]:
            if vis[i]==0:
                self.dfs(vis,adj,i,stack)
        stack.append(node)
        
    def dfsnew(self,node,vis,adj):
        vis[node]=1
        for i in adj[node]:
            if vis[i]==0:
                self.dfsnew(i,vis,adj)
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## [Strongly Connected Components (Kosaraju's Algo)](https://practice.geeksforgeeks.org/problems/strongly-connected-components-kosarajus-algo/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
