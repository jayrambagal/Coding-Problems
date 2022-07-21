## Lucky Number
Lucky numbers are subset of integers. Rather than going into much theory, let us see the process of arriving at lucky numbers,
Take the set of integers
1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19,……
First, delete every second number, we get following reduced set.
1, 3, 5, 7, 9, 11, 13, 15, 17, 19,…………
Now, delete every third number, we get
1, 3, 7, 9, 13, 15, 19,….….
Continue this process indefinitely……
Any number that does NOT get deleted due to above process is called “lucky”.

## Example 1


```bash
N = 5
Output: 0
Explanation: 5 is not a lucky number 
as it gets deleted in the second 
iteration.

```

## Solution 1 (Recursion)

```Python
class Solution:
    def isLucky(self, n): 
        return self.check(n,2)
        
    def check(self, n,c):
        
        if(c<=n):
            
            if n%c==0:
                c=2
                return False;
            
            return self.check(n-n//c,c+1)
        
        else:
            return True
```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Lucky Number](https://practice.geeksforgeeks.org/problems/lucky-numbers2911/1)
