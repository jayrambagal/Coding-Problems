## BFS of graph
Given a directed graph. The task is to do Breadth First Traversal of this graph starting from 0.

Note: One can move from node u to node v only if there's an edge from u to v and find the BFS traversal 

of the graph starting from the 0th vertex, from left to right according to the graph. Also, you should only 

take nodes directly or indirectly connected from Node 0 in consideration.

## Example 

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/203903454-e7d383ca-9940-44da-bcbc-d199c5740cdf.png)

```bash
Output: 0 1 2 3 4
Explanation: 
0 is connected to 1 , 2 , 3.
2 is connected to 4.
so starting from 0, it will go to 1 then 2
then 3.After this 2 to 4, thus bfs will be
0 1 2 3 4.

```

## Solution 

```python
class Solution:
    def bfsOfGraph(self, V, adj):
        
        visited = set()
        ans = []
        q = []
        
        q.append(0)
        visited.add(0)
        
        while q:
            m = q.pop(0)
            ans.append(m)
            for i in adj[m]:
                if i not in visited:
                    q.append(i)
                    visited.add(i)
                    
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Geeksforgeeks
[BFS of graph](https://practice.geeksforgeeks.org/problems/bfs-traversal-of-graph/1?page=1&difficulty[]=0&category[]=Graph&sortBy=submissions)
