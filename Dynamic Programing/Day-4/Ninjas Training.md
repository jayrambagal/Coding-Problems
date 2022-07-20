## Largest square formed in a matrix
Ninja is planing this ‘N’ days-long training schedule. Each day, he can perform any one of these three activities. 
(Running, Fighting Practice or Learning New Moves). Each activity has some merit points on each day. As Ninja has 
to improve all his skills, he can’t do the same activity in two consecutive days. Can you help Ninja find out the 
maximum merit points Ninja can earn?

You are given a 2D array of size N*3 ‘POINTS’ with the points corresponding to each day and activity. Your task is 
to calculate the maximum number of merit points that Ninja can earn.

## Example
```bash
Input: n = 3

1 2 5 
3 1 1
3 3 3
Output: 11

```

## Solution 1 (Recursion)

```Python

from typing import *

def ninjaTraining(n: int, points: List[List[int]]) -> int:
    
    return solve(n-1,3,points)

def solve(day,last,points):
    
    if day==0:                    # Base case
        maxx = 0
        for i in range(0,3):
            if i != last:
                maxx = max(maxx,points[0][i])
        return maxx
        
    # recursive main
    
    maxx = 0
    for i in range(0,3):
        if i != last:
            point = points[day][i] + solve(day-1,i,points)  # --> changes in 2 arguments here we can use 2d dp.
            maxx = max(maxx,point)
                
    return maxx
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
from typing import *

def ninjaTraining(n: int, points: List[List[int]]) -> int:
    dp = [ [ -1 for _ in range(4) ]  for __ in range(n+1) ]
    return solve(n-1,3,points,dp)

def solve(day,last,points,dp):
    
    if day==0:
        maxx = 0
        for i in range(0,3):
            if i != last:
                maxx = max(maxx,points[0][i])
        return maxx
    
    if dp[day][last] != -1: 
      return dp[day][last]
      
    maxx = 0
    for i in range(0,3):
        if i != last:
            point = points[day][i] + solve(day-1,i,points,dp)
            maxx = max(maxx,point)
            dp[day][last] = maxx 
            
    return dp[day][last] 
```
### Complexity
 
```bash
Time Complexity: O(N*4*3)
Space Complexity: O(N) + O(N*4)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python

```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python


```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Ninjas training](https://www.codingninjas.com/codestudio/problems/ninja-s-training_3621003?source=youtube&campaign=striver_dp_videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_dp_videos&leftPanelTab=1)
