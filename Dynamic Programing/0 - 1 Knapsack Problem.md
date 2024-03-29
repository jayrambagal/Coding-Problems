## Knapsack Problem

You are given weights and values of N items, put these items in a knapsack of capacity W to get the maximum total value in the knapsack. Note that we have only one quantity of each item.
In other words, given two integer arrays val[0..N-1] and wt[0..N-1] which represent values and weights associated with N items respectively. Also given an integer W which represents knapsack capacity, find out the maximum value subset of val[] such that sum of the weights of this subset is smaller than or equal to W. You cannot break an item, either pick the complete item or dont pick it (0-1 property).
#### Example
```bash

Input:
N = 3
W = 4
values[] = {1,2,3}
weight[] = {4,5,1}
Output: 3

Input:
N = 3
W = 3
values[] = {1,2,3}
weight[] = {4,5,6}
Output: 0



```
### Solution 

```python
class Solution:
    
   
    def knapSack(self,weight, wt, val, n):
        
       
        return self.solve(weight,wt,val,n-1)
            
    def solve(self,weight,wt,val,n):
        
        if n==0:
            if wt[0] <= weight:return val[0]
            else:return 0
            
        include = 0    
        if wt[n]<=weight:
            
            include = val[n] + self.solve(weight-wt[n],wt,val,n-1)
            
        exclude = 0 + self.solve(weight,wt,val,n-1)
        
        return max(include,exclude)
       
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution 

```python
class Solution:

    def knapSack(self,weight, wt, val, n):
        
        dp = [[-1 for x in range(weight + 1)] for x in range(n + 1)]
        return self.solve(weight,wt,val,n-1,dp)
            
    def solve(self,weight,wt,val,n,dp):
        
        if n==0:
            if wt[0] <= weight:return val[0]
            else:return 0
            
        if dp[n][weight] != -1:
            return dp[n][weight]
            
        include = 0    
        if wt[n]<=weight:
            
            include = val[n] + self.solve(weight-wt[n],wt,val,n-1,dp)
            
        exclude = 0 + self.solve(weight,wt,val,n-1,dp)
        
        dp[n][weight] = max(include,exclude)
        
        return dp[n][weight]
        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+O(n) 
```
## Solution tabulation
```python
class Solution:
    
    #Function to return max value that can be put in knapsack of capacity W.
    def knapSack(self,W, wt, val, n):
       
       dp = [[0 for i in range(W+1)]for j in range(n+1)]
       
       for i in range(1,n+1):
           for j in range(1,W+1):
               dp[i][j] = dp[i-1][j]
               
               if j>=wt[i-1]:
                   if (dp[i-1][j] < dp[i-1][j-wt[i-1]] + val[i-1] ):
                       dp[i][j] = dp[i-1][j-wt[i-1]] + val[i-1]
       return dp[-1][-1]
```

[Knapsack Problem](https://practice.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1)


