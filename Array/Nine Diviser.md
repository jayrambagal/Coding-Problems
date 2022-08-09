## Nine Diviser

Find the count of numbers less than equal to N having exactly 9 divisors.


 
## Example 1


```bash


Input:
N = 100
Output:
2
Explanation:
The two numbers which have 
exactly 9 divisors are 36 and 100.

Input:
N = 1000
Output:
8 
Explanation:
The numbers are:
36 100 196 225 256 441 484 676
```

## Solution 1 (recursion) 
```Python

class Solution:
    def nineDivisors(self, n):
        
        c = 0
        for i in range(1, n + 1) :
            if (self.solve(i) == 9):
                c += 1
        return c
    
    def solve(self,n):
        count =0 
        for i in range(1,n+1):
            if (n%i==0):
                count+=1
        return count
        
```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity :O(1)
```
