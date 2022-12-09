## Number of Ways to Arrive at Destination
```
You are in a city that consists of n intersections numbered from 0 to n - 1 with bi-directional roads between some intersections. 
The inputs are generated such that you can reach any intersection from any other intersection and that there is at most one road 
between any two intersections.You are given an integer n and a 2D integer array roads where roads[i] = [ui, vi, timei] means that 
there is a road between intersections ui and vi that takes timei minutes to travel. You want to know in how many ways you can travel 
from intersection 0 to intersection n - 1 in the shortest amount of time. Return the number of ways you can arrive at your destination 
in the shortest amount of time. Since the answer may be large, return it modulo 109 + 7.
```
## Example 

```bash
Input:
n=7, m=10
edges= [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]

Output:
4
Explaination:

The four ways to get there in 7 minutes are:
- 0  6
- 0  4  6
- 0  1  2  5  6
- 0  1  3  5  6
```

## Solution

```python
import heapq
from typing import List
from collections import defaultdict
import sys
class Solution:
    def countPaths(self, n: int, roads: List[List[int]]) -> int:
        
        des = n-1
        adj = defaultdict(list)
        
        for u,v,wt in roads:
            adj[u].append((v,wt))
            adj[v].append((u,wt))
            
        ways = [0]*n
        distance = [9999999]*n
        distance[0] = 0
        q = [(0,0)]
        
        while q:
            node,wt = heapq.heappop(q)
            
            for i,j in adj[node]:
                
                if distance[i] > distance[node]+j:
                    distance[i] = distance[node]+j
                    ways[i] +=1
                    heapq.heappush(q,(i,j))
                elif distance[i] == distance[node]+j:
                    ways[i] += ways[node]
                    
        return ways[n-1]
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Number of Ways to Arrive at Destination](https://practice.geeksforgeeks.org/problems/number-of-ways-to-arrive-at-destination/1)
