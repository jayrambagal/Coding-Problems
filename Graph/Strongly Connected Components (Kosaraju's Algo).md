## Strongly Connected Components (Kosaraju's Algo)
There are a total of n tasks you have to pick, labeled from 0 to n-1. Some tasks may have prerequisites tasks, 

for example to pick task 0 you have to first finish tasks 1, which is expressed as a pair: [0, 1]

Given the total number of n tasks and a list of prerequisite pairs of size m. Find a ordering of tasks you should pick to finish all tasks.

Note: There may be multiple correct orders, you just need to return one of them. If it is impossible to finish all tasks, return an empty 
array. Returning any correct order will give the output as 1, whereas any invalid order will give the output 0.
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
