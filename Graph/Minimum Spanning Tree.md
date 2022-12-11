## Minimum Spanning Tree
Given a weighted, undirected and connected graph of V vertices and E edges. The task 

is to find the sum of weights of the edges of the Minimum Spanning Tree.

## Example 

```bash
Input:
3 3
0 1 5
1 2 3
0 2 1
```
![image](https://user-images.githubusercontent.com/94613732/204126158-433e516a-7314-4643-8836-dfe7a708d86e.png)

```
Output:
4
Explanation:
```
![image](https://user-images.githubusercontent.com/94613732/204126164-c3645a7a-4a47-42ea-add1-355d19980269.png)

```

The Spanning Tree resulting in a weight
of 4 is shown above.

```

## Solution (prims algo)

```python
from collections import defaultdict,deque
import heapq
import sys
class Solution:
        
    def spanningTree(self, V, graph):
        
        ans = 0 
        visited = [0]*V
        q = [(0,0)]
        
        while q:
            wt,node = heapq.heappop(q)
            
            if visited[node]==1:
                continue
        
            visited[node] = 1
            ans+=wt
            
            for new_node,new_weight in graph[node]:
                
                if visited[new_node]==0:
                    heapq.heappush(q,(new_weight,new_node))
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(E*logE) + O(E*logE)
Space Complexity : O(E)
```
## Geeksforgeeks
[Minimum Spanning Tree](https://practice.geeksforgeeks.org/problems/minimum-spanning-tree/1?page=1&category[]=Graph&sortBy=submissions)
