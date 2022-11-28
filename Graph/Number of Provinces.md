## Number of Provinces
Given an undirected graph with V vertices. We say two vertices u and v belong to a single province if there 

is a path from u to v or v to u. Your task is to find the number of provinces.

Note: A province is a group of directly or indirectly connected cities and no other cities outside of the group.

## Example 

```bash
Input:
[
 [1, 0, 1],
 [0, 1, 0],
 [1, 0, 1]
]

Output:
2
Explanation:
The graph clearly has 2 Provinces [1,3] and [2]. As city 1 and city 3 has a path 
between them they belong to a single province. City 2 has no path to city 1 or city 3 
hence it belongs to another province.
```


## Solution

```python
class Solution:
    
    def numProvinces(self, adj, V):
        graph = [[] for i in range(V)]
        for i in range(V):
            for j in range(V):
                if i!=j and adj[i][j]==1:
                    graph[i].append(j)
                    graph[j].append(i)
                    
        visit = [0]*V
        count = 0
        
        for i in range(V):
            if visit[i]==0:
                count+=1
                self.dfs(visit,i,graph)
        return count
                
    def dfs(self,visit,node,graph):
        visit[node]=1
        
        for i in graph[node]:
            if visit[i]==0:
                self.dfs(visit,i,graph)
```
#### Complexity
```bash
Time Complexity : O(V) + O(V+2E)
Space Complexity : O(V) + O(V) --> visited + recursion stack
```
## Geeksforgeeks
[Number of Provinces](https://practice.geeksforgeeks.org/problems/number-of-provinces/1)
