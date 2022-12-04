## Course Schedule
There are a total of n tasks you have to pick, labeled from 0 to n-1. Some tasks may have prerequisites tasks, 

for example to pick task 0 you have to first finish tasks 1, which is expressed as a pair: [0, 1]

Given the total number of n tasks and a list of prerequisite pairs of size m. Find a ordering of tasks you should pick to finish all tasks.

Note: There may be multiple correct orders, you just need to return one of them. If it is impossible to finish all tasks, return an empty 
array. Returning any correct order will give the output as 1, whereas any invalid order will give the output 0.
## Example 

```bash
Input:
n = 2, m = 1
prerequisites = {{1, 0}}
Output:
1
Explanation:
The output 1 denotes that the order is
valid. So, if you have, implemented
your function correctly, then output
would be 1 for all test cases.
One possible order is [0, 1].


Input:
n = 4, m = 4
prerequisites = {{1, 0},
                 {2, 0},
                 {3, 1},
                 {3, 2}}
Output:
1
Explanation:
There are a total of 4 tasks to pick.
To pick task 3 you should have finished
both tasks 1 and 2. Both tasks 1 and 2
should be pick after you finished task 0.
So one correct task order is [0, 1, 2, 3].
Another correct ordering is [0, 2, 1, 3].
Returning any of these order will result in
a Output of 1.
```

## Solution

```python
from collections import defaultdict

class Solution:
    def findOrder(self, N, m, pre):
        d,ind,q,res = defaultdict(list),[0]*(N),[],[]
        for i,j in pre:
            d[j].append(i)
            ind[i]+=1
        
        for i in range(N):
            if ind[i]==0:
                q.append(i)
                res.append(i)
        c = 0
        while q:
            x = q.pop(0)
            for out in d[x]:
                ind[out]-=1
                if ind[out]==0:
                    q.append(out)
                    res.append(out)
            c+=1
        if c==N:
            return res
        return []
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Course Schedule](https://practice.geeksforgeeks.org/problems/course-schedule/1)
