## partition equal subset

Given an array arr[] of size N, check if it can be partitioned into two parts such that the sum of elements in both parts is the same.
#### Example
```baInput: N = 3
arr = {1, 3, 5}
Output: NO
Explanation: This array can never be 
partitioned into two such parts.


Input: N = 4
arr = {1, 5, 11, 5}
Output: YES
Explanation: 
The two parts are {1, 5, 5} and {11}.



```
### Solution 

```python
class Solution:
    def equalPartition(self, N, arr):
        total = 0
        for i in range(N):
            total +=arr[i]
            
        if total%2 != 0:
            return 0
            
        target = total//2
        
        return self.solve(0,arr,N,target)
        
    def solve(self,index,arr,n,target):
        
        if index>=n:
            return 0
            
        if target <0:
            return 0
            
        if target == 0:
            return 1
            
        inc = self.solve(index+1,arr,n,target-arr[index])
        exc = self.solve(index+1,arr,n,target)
        
        return inc or exc
        
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
    def equalPartition(self, N, arr):
        total = 0
        for i in range(N):
            total +=arr[i]
            
        if total%2 != 0:
            return 0
            
        target = total//2
        
        dp = [[-1 for _ in range(target+1)]for __ in range(N)]
        
        return self.solve(0,arr,N,target,dp)
        
    def solve(self,index,arr,n,target,dp):
        
        if index>=n:
            return 0
            
        if target <0:
            return 0
            
        if target == 0:
            return 1
            
        if dp[index][target] != -1:
            return dp[index][target]
            
        inc = self.solve(index+1,arr,n,target-arr[index],dp)
        exc = self.solve(index+1,arr,n,target,dp)
        
        dp[index][target] = inc or exc
        
        return dp[index][target]
        
```
```
### Complexity
```bash
Time Complexity = O(n*summ)
Space Complexity = O(n*summ)+O(n) 
```
        
[Partition Subset Sum](https://practice.geeksforgeeks.org/problems/subset-sum-problem2014/1)
```

