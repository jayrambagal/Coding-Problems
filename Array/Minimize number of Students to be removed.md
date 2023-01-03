## Minimize number of Students to be removed
```
N Students of different heights are attending an assembly. The heights of the students are represented by an array H[]. 

The problem is that if a student has less or equal height than the student standing in front of him, then he/she cannot see 

the assembly. Find the minimum number of students to be removed such that maximum possible number of students can see the assembly.
 
```

## Example 
```bash
Input:
N = 6
H[] = {9, 1, 2, 3, 1, 5}
Output:
2
Explanation:
We can remove the students at 0 and 4th index.
which will leave the students with heights
1,2,3, and 5.


Input:
N = 3
H[] = {1, 2, 3} 
Output :
0
Explanation:
All of the students are able to see the
assembly without removing anyone.

```

## Solution 

```python
from bisect import bisect_left
class Solution:
    def removeStudents(self, H, N):
        
        ans=[H[0]]
        for i in range(1, N):
            if H[i]>ans[-1]:
                ans.append(H[i])
            else:
                ans[bisect_left(ans, H[i])]=H[i]
                
        return N-len(ans)
 ```
#### Complexity
```bash
Time Complexity :O(NlogN + n)
Space Complexity : O(1)
```

 

## Geeksforgeeks
[Minimize number of Students to be removed](https://practice.geeksforgeeks.org/problems/7d0fa4007b8eabadc404fcc9fa917aa52982aa96/1)
