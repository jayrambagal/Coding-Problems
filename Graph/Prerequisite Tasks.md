## Prerequisite Tasks
There are a total of N tasks, labeled from 0 to N-1. Some tasks may have prerequisites, 

for example to do task 0 you have to first complete task 1, which is expressed as a pair: [0, 1]

Given the total number of tasks N and a list of prerequisite pairs P, find if it is possible to finish all tasks.

## Example 

```bash
Input: 
N = 4, P = 3
prerequisites = {{1,0},{2,1},{3,2}}
Output:
Yes
Explanation:
To do task 1 you should have completed
task 0, and to do task 2 you should 
have finished task 1, and to do task 3 you 
should have finished task 2. So it is possible.

Input:
N = 2, P = 2
prerequisites = {{1,0},{0,1}}
Output:
No
Explanation:
To do task 1 you should have completed
task 0, and to do task 0 you should
have finished task 1. So it is impossible.

```

## Solution 

```python
from collections import deque
class Solution:
    def isPossible(self,N,prerequisites):
        #code here
        indeg = [0]*N
        adj = [[] for i in range(N)]
        for (src, dest) in prerequisites:
            adj[src].append(dest)
            indeg[dest] += 1
        
        q = deque([]) 
        for node in range(N):
            if indeg[node]==0:
                q.append(node)
 
        while q:
            node = q.popleft()
            for nei in adj[node]:
                indeg[nei] -= 1
                if indeg[nei] == 0:
                    q.append(nei)
       
       
        for i in range(N):
            if indeg[i] != 0:
                return False
        return True
```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```

## Geeksforgeeks
[Prerequisite Tasks](https://practice.geeksforgeeks.org/problems/prerequisite-tasks/1)
