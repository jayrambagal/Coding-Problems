## Maximize The Cut Segments
Given an integer N denoting the Length of a line segment. You need to cut the line segment in such a way that the cut length of a line segment each time is either x , y or z. Here x, y, and z are integers.
After performing all the cut operations, your total number of cut segments must be maximum.
## Example 1


```bash
Input:
N = 4
x = 2, y = 1, z = 1
Output: 4


N = 5
x = 5, y = 3, z = 2
Output: 2
```

## Solution 1 (Recursion)

```Python

import sys

class Solution:
    
    
    def maximizeTheCuts(self,n,x,y,z):
        
        ans = self.solve(n,x,y,z)
        if ans <0:
            return 0
        else:
            return ans
        
    def solve(self,n,x,y,z):
        
        if n==0:
            return 0
            
        if n<0:
            return -sys.maxsize
        
        a = self.solve(n-x,x,y,z) + 1    # +1 is count of segments
        b = self.solve(n-y,x,y,z) + 1
        c = self.solve(n-z,x,y,z) + 1
        
        ans = max(a,b,c)
        return ans
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python



```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> space optimization
```Python

```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Maximize The Cut Segments](https://practice.geeksforgeeks.org/problems/cutted-segments1642/1)
