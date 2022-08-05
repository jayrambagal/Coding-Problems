## Knapsack Problem  --> 2D DP
You are given weights and values of N items, put these items in a knapsack of capacity W to get the maximum total value in the knapsack. Note that we have only one quantity of each item.
In other words, given two integer arrays val[0..N-1] and wt[0..N-1] which represent values and weights associated with N items respectively. Also given an integer W which represents knapsack capacity, find out the maximum value subset of val[] such that sum of the weights of this subset is smaller than or equal to W. You cannot break an item, either pick the complete item or dont pick it (0-1 property).
## Example 1


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

## Solution 1 (Recursion)

```Python

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
        
        ans = max(include,exclude)
        
        return ans
        
```
### Complexity
 
```bash
Time Complexity : Expo
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
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
Time Complexity : O(n*weight)
Space Complexity : O(n*weight)+O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```Python
class Solution:
    
    def knapSack(self,weight, wt, val, n):
        
        dp = [[0 for _ in range(weight+1)]for __ in range(n+1)]
        
        for i in range(wt[0],weight+1):
            dp[0][i] = val[0]
    
    
        for i in range(1,n):
    
            for j in range(0,weight+1):
            
                notTaken = 0 + dp[i-1][j];
            
                taken = -sys.maxsize
                if(wt[i] <= j):
                    taken = val[i] + dp[i-1][j - wt[i]]
                
                dp[i][j] = max(notTaken, taken)
      
        return dp[n-1][weight]

```
```bash
Time Complexity : O(n*weight)
Space Complexity : O(n*weight)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python
class Solution:
    
    def knapSack(self,weight, wt, val, n):
        
        prev = [0]*(weight+1)
        
        for i in range(wt[0],weight+1):
            prev[i] = val[0]
    
    
        for i in range(1,n):
    
            for j in range(weight,-1,-1):
            
                notTaken = 0 + prev[j]
            
                taken = -sys.maxsize
                if(wt[i] <= j):
                    taken = val[i] + prev[j-wt[i]]
                
                prev[j] = max(notTaken, taken)
      
        return prev[weight]

```
```bash
Time Complexity : O(n*weight)
Space Complexity : O(1)
```
## GeeksforGeeks
[Knapsack Problem](https://practice.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1)
