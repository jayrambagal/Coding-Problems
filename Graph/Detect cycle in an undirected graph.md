## Detect cycle in an undirected graph
Given an undirected graph with V vertices and E edges, check whether it contains any cycle or not. 

## Example 

```bash
Input:
V = 5, E = 5
adj = {{1}, {0, 2, 4}, {1, 3}, {2, 4}, {1, 3}} 
```
![image](https://user-images.githubusercontent.com/94613732/203913784-78504f52-5ed7-4847-a0d6-11e08793f1ba.png)

```bash
Output : 1

```

## Solution (BFS)

```python
from typing import List
class Solution:
    
    def isCycle(self, V: int, adj: List[List[int]]) -> bool:
        
        v = [0] * V

        for i in range(V):
            if v[i]==0:
                q = []
                v[i] = -1
                q.append(i)
                
                while q:
                    
                    vrtx = q.pop(0)
                    for x in adj[vrtx]:
                        if v[x]==0:
                            q.append(x)
                            v[x] = vrtx
                        elif v[x] and (x != v[vrtx]):
                            return 1
                            
        return 0
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Solution (DFS)

```python

from collections import defaultdict
from typing import List
class Solution:
    
    def isCycle(self, V: int, adj: List[List[int]]) -> bool:
        
        ver=[False]*(V)
        
        for i in range(V):
            if ver[i]==False:
                if self.cycle(ver,adj,i,-1) == True:
                    return True
        return False
    
    def cycle(self,ver,adj,s,parent):
        ver[s]=True
        for j in adj[s]:
            if ver[j]==False:
                if self.cycle(ver,adj,j,s)==True:
                    return True
            elif j!=parent:
                return True
        return False
     

        
        

 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Geeksforgeeks
[Detect cycle in an undirected graph](https://practice.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1?page=1&difficulty[]=0&difficulty[]=1&status[]=unsolved&category[]=Graph&sortBy=submissions)
