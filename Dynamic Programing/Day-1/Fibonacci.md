## Fibonacci Number
Given a number n. find the nth fibonacci number.
## Example 1


```bash
Input 1:
n = 3 
Output: 2

n = 5
Output: 5

```

## Solution 1 (Recursion)

```Python

def fibonacci(n):
    
    if n==1:
        return 1
    if n==0: return 0
    
    return fibonacci(n-1)+fibonacci(n-2)
    
n=3
print(fibonacci(n))

```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python

def fibonacci(n,dp):
    
    if n==1:
        return 1
    if n==0: return 0
    
    if dp[n]!= -1:
        return dp[n]
    
    dp[n]=fibonacci(n-1,dp)+fibonacci(n-2,dp)
    
    return dp[n]
    
n=3
dp=[-1]*(n+1)
print(fibonacci(n,dp))

```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation and space optimization
```Python
def fibonacci(n):
    prev1 = 1
    prev2 = 0
    
    for i in range(2,n+1):
        curr = prev1+prev2
        prev2=prev1
        prev1=curr
        
    return prev1
        
n=5
print(fibonacci(n))
```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[]()
