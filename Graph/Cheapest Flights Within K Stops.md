## Cheapest Flights Within K Stops
There are n cities and m edges connected by some number of flights. You are given an array flights where flights[i] = [fromi, toi, pricei] indicates 
that there is a flight from city fromi to city toi with cost pricei.

You are also given three integers src, dst, and k, return the cheapest price from src to dst with at most k stops. If there is no such route, return -1.

## Example 

```bash
Example 1:
Input:
n = 4
flights = [[0,1,100],[1,2,100],[2,0,100],[1,3,600],[2,3,200]]
src = 0
dst = 3
k = 1
Output:
700
Explaination:
The optimal path with at most 1 stop from city 0 to 3 is marked in red and has cost 100 + 600 = 700.
Note that the path through cities [0,1,2,3] is cheaper but is invalid because it uses 2 stops.


```

## Solution (Djikstra Algo using deque)

```python
#User function Template for python3
from typing import List
from collections import deque,defaultdict
class Solution:
    def CheapestFLight(self,n,flights,src,dst,k):
        
        adj = defaultdict(list)
        def add(u,v,dis):
            adj[u].append((v,dis))
            
        for i in flights:
            add(i[0],i[1],i[2])
        
        ans = 99999999
        q = deque([])
        q.append((0,src,0)) #count, source_node, distance
        
        while q:
            count,node,distance = q.popleft()
            
            for i,j in adj[node]:
                
                if count<=k:
                    q.append((count+1,i,distance+j))
                if count<=k and i==dst:
                    ans = min(ans,distance+j)
        return ans



 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```

## Solution (Djikstra Algo using heap or priorty queue)

```python
#User function Template for python3
import heapq
from typing import List
from collections import deque,defaultdict
class Solution:
    def CheapestFLight(self,n,flights,src,dst,k):
        
        graph = defaultdict(list)
        for u, v, w in flights:
            graph[u].append((v, w))

        # dist, idx, path_len
        q = [(0, src, 1)]
        max_path_len = k + 2
        while q:
            dist, idx, path_len = heapq.heappop(q)
            if path_len > max_path_len:
                continue
            if idx == dst:
                return dist
            for v, w in graph[idx]:
                heapq.heappush(q, (dist+w, v, path_len+1))
        return -1






 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```

## Geeksforgeeks
[Cheapest Flights Within K Stops](https://practice.geeksforgeeks.org/problems/cheapest-flights-within-k-stops/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=cheapest-flights-within-k-stops)
