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
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n)+O(k) 
```
        
```
