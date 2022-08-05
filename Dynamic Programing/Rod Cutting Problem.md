## Rod Cutting Problem 
 [Rod Cutting Problem](https://www.codingninjas.com/codestudio/problems/rod-cutting-problem_800284?leftPanelTab=0)
Given a rod of length 'N' units. The rod can be cut into different sizes and each size has a cost associated with it. Determine the
maximum cost obtained by cutting the rod and selling its pieces.
#### Example
```bash
Input:
5
42 68 35 1 70 

output = 210
```
### Solution 

```python
from sys import stdin
import sys

def cutRod(price, n):
    
    return solve(price,n,n-1)

def solve(price,n,i):
    
    if i==0:
        return n*price[0]
    
    not_take = 0 + solve(price,n,i-1)
    take = -sys.maxsize
    rod = i +1
    
    if rod<=n:
        take = price[i] + solve(price,n-rod,i)
        
    return max(not_take,take)
        
```
#### Input Format
```python 
# Taking input using fast I/O.
def takeInput():
    n = int(input())

    price = list(map(int, input().strip().split(" ")))

    return price, n


# Main.
t = int(input())
while t:
    price, n = takeInput()
    print(cutRod(price, n))
    t = t-1
```
### Complexity
```bash
Time Complexity = Exponentioal
Space Complexity = 
```
### Solution (Memoiation)

```python

def cutRod(price, n):
    dp = [[-1 for _ in range(n+1)]for __ in range(n+1)]
    return solve(price,n,n-1,dp)

def solve(price,n,i,dp):
    
    if i==0:
        return n*price[0]
    
    if dp[i][n] != -1:
        return dp[i][n]
    
    not_take = 0 + solve(price,n,i-1,dp)
    take = -sys.maxsize
    rod = i +1
    
    if rod<=n:
        take = price[i] + solve(price,n-rod,i,dp)
        
    dp[i][n] =  max(not_take,take)
    
    return dp[i][n]

```
### Complexity
```bash
Time Complexity = 
Space Complexity =  
```
### Solution 

```python

```
### Complexity
```bash
Time Complexity = O()
Space Complexity = O()
```

[Rod cutting problem](https://www.codingninjas.com/codestudio/problems/rod-cutting-problem_800284?leftPanelTab=0)
