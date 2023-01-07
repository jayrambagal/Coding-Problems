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

![image](https://user-images.githubusercontent.com/94613732/211148886-72a53538-07ee-445a-b3f3-22e3da6ae8c9.png)

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

## Solution (disjoint set)
```python
class Solution:
    
    def numProvinces(self, adj, V):
        
        ds = DisjointSet(V)
        
        for i in range(V):
            for j in range(V):
                if adj[i][j]==1:
                    ds.union(i,j)
        count = 0         
        for i in range(V):
            if ds.parent[i]==i:
                count+=1
        return count
                    
       
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
Time Complexity : O(V^2) + O(4*alpha)
Space Complexity : O(V)
```
## Geeksforgeeks
[Number of Provinces](https://practice.geeksforgeeks.org/problems/number-of-provinces/1)
