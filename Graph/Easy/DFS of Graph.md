## DFS of Graph
You are given a connected undirected graph. Perform a Depth First Traversal of the graph.

Note: Use a recursive approach to find the DFS traversal of the graph starting from the 

0th vertex from left to right according to the graph.

## Example 

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/203835933-e1ff7832-933c-434d-99f7-38c151ff1e42.png)

```bash
Output: 0 2 4 3 1
Explanation: 
0 is connected to 2, 3, 1.
1 is connected to 0.
2 is connected to 0 and 4.
3 is connected to 0.
4 is connected to 2.
so starting from 0, it will go to 2 then 4,
and then 3 and 1.
Thus dfs will be 0 1 2 4 3.

```

## Solution 

```python
#User function Template for python3
class Solution:
    
    #Function to return a list containing the DFS traversal of the graph.
    def dfsOfGraph(self, V, adj):
     
        vertex=set()

        s=0

        q=[]

        def dfs(vertex,adj,s,q):

            vertex.add(s)

            q.append(s)

            for i in adj[s]:

                if i not in vertex:

                    dfs(vertex,adj,i,q)

            return q

        q=dfs(vertex,adj,s,q)

        return q 
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Geeksforgeeks
[DFS of Graph](https://practice.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
