## Minimum Multiplications to reach End
Given start, end and an array arr of n numbers. At each step, start is multiplied with any number in the 

array and then mod operation with 100000 is done to get the new start.

Your task is to find the minimum steps in which end can be achieved starting from start. If it is not possible to reach end, then return -1.
## Example 

```bash
Input:
arr[] = {2, 5, 7}
start = 3, end = 30
Output:
2
Explanation:
Step 1: 3*2 = 6 % 100000 = 6 
Step 2: 6*5 = 30 % 100000 = 30

Input:
arr[] = {3, 4, 65}
start = 7, end = 66175
Output:
4
Explanation:
Step 1: 7*3 = 21 % 100000 = 21 
Step 2: 21*3 = 6 % 100000 = 63 
Step 3: 63*65 = 4095 % 100000 = 4095 
Step 4: 4095*65 = 266175 % 100000 = 66175
```

## Solution

```python
from typing import List
from collections import deque
class Solution:
    
    def minimumMultiplications(self, arr : List[int], start : int, end : int) -> int:
        
        q = deque([])
        max_arr = [1e9]*(100000)
        max_arr[start] = 0
        
        q.append((0,start))
        
        while q:
            dis,node = q.popleft()
            
            for i in arr:
                
                new_node = (node*i)% 100000
                if max_arr[new_node] > dis+1:
                    max_arr[new_node] = dis+1
                    if new_node == end:
                        return dis+1
                    q.append((dis+1,new_node))
        return -1
 ```
#### Complexity
```bash
Time Complexity :O(10^5 * n )
Space Complexity : O(10000)
```
## Geeksforgeeks
[Minimum Multiplications to reach End](https://practice.geeksforgeeks.org/problems/minimum-multiplications-to-reach-end/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=minimum-multiplications-to-reach-end)
