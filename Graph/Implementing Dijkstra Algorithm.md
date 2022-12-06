## Implementing Dijkstra Algorithm
```
Given a weighted, undirected and connected graph of V vertices and an adjacency list adj where adj[i] is a list 
of lists containing two integers where the first integer of each list j denotes there is edge between i and j , 
second integers corresponds to the weight of that  edge . You are given the source vertex S and You to Find the 
shortest distance of all the vertex's from the source vertex S. You have to return a list of integers denoting 
shortest distance between each node and Source vertex S.

Note: The Graph doesn't contain any negative weight cycle.
```

## Example 

```bash
Input:
V = 2
adj [] = {{{1, 9}}, {{0, 9}}}
S = 0
Output:
0 9
```
```bash
Explanation :
```
![image](https://user-images.githubusercontent.com/94613732/204086503-e384c469-f3d4-49ad-a168-afa6f9258c6d.png)
```
The source vertex is 0. Hence, the shortest 
distance of node 0 is 0 and the shortest 
distance from node 1 is 9.

```
```bash
Input:
V = 3, E = 3
adj = {{{1, 1}, {2, 6}}, {{2, 3}, {0, 1}}, {{1, 3}, {0, 6}}}
S = 2
Output:
4 3 0
Explanation:
```
![image](https://user-images.githubusercontent.com/94613732/204086576-36d11d93-a8bc-4638-b948-552948fdfe40.png)

```
For nodes 2 to 0, we can follow the path-
2-1-0. This has a distance of 1+3 = 4,
whereas the path 2-0 has a distance of 6. So,
the Shortest path from 2 to 0 is 4.
The shortest distance from 0 to 1 is 1 .

```

## Solution 

```python
class Solution:

    def dijkstra(self, V, adj, S):

        dis = [99999999]*V
        stack = []
        
        dis[S] = 0
        stack.append((S,0))
        
        while stack:
            top_node , node_dis  = stack.pop()

            for neber, diss in adj[top_node]:
                
                if ((node_dis + diss) < dis[neber]):
                    
                    for i in stack:
                        if i[0] == neber and i[1] == diss:
                            stack.pop(i)
                            
                    dis[neber] = node_dis + diss
                    
                    stack.append((neber,dis[neber]))
        return dis
 ```
#### Complexity
```bash
Time Complexity :O(E*V)
Space Complexity : O(V)
```
## Geeksforgeeks
[Implementing Dijkstra Algorithm](https://practice.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1)
