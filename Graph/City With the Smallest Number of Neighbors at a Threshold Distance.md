## City With the Smallest Number of Neighbors at a Threshold Distance

There are n cities numbered from 0 to n-1. Given the array edges where edges[i] = [fromi , toi ,weighti]  represents 

a bidirectional and weighted edge between cities fromi and toi, and given the integer distance Threshold. You need to 

find out a city with the smallest number of cities that are reachable through some path and whose distance is at most 

Threshold Distance, If there are multiple such cities, our answer will be the city with the greatest number.

Note: that the distance of a path connecting cities i and j is equal to the sum of the edges' weights along that path.
## Example 

```bash
Input:
N=4,M=4
edges = [[0,1,3],[1,2,1],[1,3,4],[2,3,1]]
distanceThreshold = 4
Output:3
Explaination:The neighboring cities at a distanceThreshold = 4 for each city are:
City 0 -> [City 1, City 2] 
City 1 -> [City 0, City 2, City 3] 
City 2 -> [City 0, City 1, City 3] 
City 3 -> [City 1, City 2] 
Cities 0 and 3 have 2 neighboring cities at a distanceThreshold = 4, but we have to return city 3 since it has the greatest number.
```

## Solution

```python
from typing import List
from collections import defaultdict,deque
class Solution:
    def findCity(self, n : int, m : int, edges : List[List[int]], distanceThreshold : int) -> int:

        dist = [[float("inf") for _ in range(n)] for _ in range(n)]

        for a in range(n):
            dist[a][a] = 0

        for src, dst, w in edges:
            dist[src][dst] = w
            dist[dst][src] = w

        for via in range(n):
            for i in range(n):
                for j in range(n):
                    if dist[i][via] == float('inf') or dist[via][j] == float('inf'):
                        continue
                    dist[i][j] = min(dist[i][j], (dist[i][via] + dist[via][j]))

        res = -1
        cityCount = n
        for x in range(n):
            currCityCount = 0
            for y in range(n):
                if x == y:
                    continue
                if dist[x][y] <= distanceThreshold:
                    currCityCount += 1
            if currCityCount <= cityCount:
                cityCount = currCityCount
                res = x

        return res
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[City With the Smallest Number of Neighbors at a Threshold Distance](https://practice.geeksforgeeks.org/problems/city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/1?page=1&category[]=Disjoint%20Set&sortBy=submissions)
