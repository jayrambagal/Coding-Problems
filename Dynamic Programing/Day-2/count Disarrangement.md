## Disarrangement of balls
You are given N balls numbered from 1 to N and there are N baskets numbered from 1 to N in front of you, the ith basket is meant for the ith ball. Calculate the number of ways in which no ball goes into its respective basket.
## Example 1


```bash
Input: N = 2
Output: 1

Input: 3
Output: 2
Explanation: The (number-basket) pairs are 
[(1-3),(2-1),(3-2)] and [(1-2),(2-3),(3-2)].
```

## Solution 1 (Recursion)

```Python
class Solution:
    def disarrange(self, n):
        
        if n==1:return 0
            
        if n==2:return 1
        
        ans = (n-1)*(self.disarrange(n-1) + self.disarrange(n-2))
        
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
[Disarrangement of balls](https://practice.geeksforgeeks.org/problems/dearrangement-of-balls0918/1)
