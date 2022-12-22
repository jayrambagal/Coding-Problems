## Zero Sum Subarrays
```
Given a 5x6 snakes and ladders board, find the minimum number of dice throws required to reach the 
destination or last cell (30th cell) from the source (1st cell).

You are given an integer N denoting the total number of snakes and ladders and an array 
arr[] of 2*N size where 2*i and (2*i + 1)th values denote the starting and ending point respectively 
of ith snake or ladder. The board looks like the following.
Note: Assume that you have complete control over the 6 sided dice. No ladder starts from 1st cell.
```

![image](https://user-images.githubusercontent.com/94613732/209076201-fb0c8a1e-62d3-4e04-8bab-6b5883263b3d.png)

## Example 
```bash
Input:
N = 8
arr[] = {3, 22, 5, 8, 11, 26, 20, 29, 
       17, 4, 19, 7, 27, 1, 21, 9}
Output: 3
Explanation:
The given board is the board shown
in the figure. For the above board 
output will be 3. 
a) For 1st throw get a 2. 
b) For 2nd throw get a 6.
c) For 3rd throw get a 2.

```


## Solution

``` python
from collections import deque
class Solution:
    def minThrow(self, N, move):
        
        
        parent = [-1]*35
        
        for i in range(0,N*2,2):
            parent[move[i]] = move[i+1]
            
        q = deque()
        q.append((1,0))
        
        visited = set()
        visited.add(1)
        while q:
            
            node,dis = q.popleft()
            
            if node == 30:
                return dis
                
            
             
            for i in range(node+1,node+7):
                if i<31:
                    if i not in visited:
                        visited.add(i)
                        if parent[i]==-1:
                            q.append((i,dis+1))
                        elif parent[i]!=-1:
                            q.append((parent[i],dis+1))
    
                else:
                    break
        return -1
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```



## Geeksforgeeks
[Snake and Ladder Problem](https://practice.geeksforgeeks.org/problems/snake-and-ladder-problem4816/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Graph&sortBy=submissions)
