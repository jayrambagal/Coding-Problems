## Subset sum equal to Target

Given an array of non-negative integers, and a value sum, determine if there is a subset of the given set with sum equal to given sum. 

#### Example
```bash
Input:
N = 6
arr[] = {3, 34, 4, 12, 5, 2}
sum = 9
Output: 1 
Explanation: Here there exists a subset with
sum = 9, 4+3+2 = 9.

```

![image](https://user-images.githubusercontent.com/94613732/210337228-d277758a-dbfa-4f9e-af78-eafbbf574a64.png)

### Solution 

```python
class Solution:
    def isSubsetSum (self, N, arr, summ):
        return self.solve(N-1,arr,summ)
        
    def solve(self,n,arr,summ):
        
        if summ==0:
            return True
            
        if n==0:
            return arr[n] == summ
            
        exclude = self.solve(n-1,arr,summ)
        include = False
        if summ>=arr[n]:
            include = self.solve(n-1,arr,summ-arr[n])
            
        return include or exclude
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution 

```python
### Solution 

```python
class Solution:
    def isSubsetSum (self, N, arr, summ):
        dp =[[-1 for _ in range(summ+1)]for __ in range(N+1)]
        return self.solve(N-1,arr,summ,dp)
        
    def solve(self,n,arr,summ,dp):
        
        if summ==0:
            return True
            
        if n==0:
            return arr[n] == summ
            
        if dp[n][summ] != -1:
            return dp[n][summ]
            
        exclude = self.solve(n-1,arr,summ,dp)
        include = False
        if summ>=arr[n]:
            include = self.solve(n-1,arr,summ-arr[n],dp)
            
        dp[n][summ] = include or exclude
        
        return dp[n][summ] 
        
```
```
### Complexity
```bash
Time Complexity = O(n*summ)
Space Complexity = O(n*summ)+O(n) 
```
        
[Subset sum of target](https://practice.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1)
