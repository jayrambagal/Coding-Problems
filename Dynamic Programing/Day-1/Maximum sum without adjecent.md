## Max Sum without Adjacents
Given an array Arr of size N containing positive integers. Find the maximum sum of a subsequence such that no two numbers in the sequence should be adjacent in the array.
## Example 1


```bash
N = 6
Arr[] = {5, 5, 10, 100, 10, 5}
Output: 110
Explanation: If you take indices 0, 3
and 5, then Arr[0]+Arr[3]+Arr[5] =
5+100+5 = 110.

```

## Solution 1 (Recursion)

```Python

class Solution:
	
	def findMaxSum(self,arr, n):
	    
	    ans = self.solve(arr,n-1)
	    return ans
	    
    def solve(self,arr,n):
        
        if n==0: return arr[0]
        
        if n<0: return 0
        
        include = self.solve(arr,n-2)+arr[n]
        exclude = self.solve(arr,n-1)+ 0 
        
        return max(include,exclude)
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python

class Solution:
	
	def findMaxSum(self,arr, n):
	    
	    dp=[-1]*(n+1)
	    ans = self.solve(arr,n-1,dp)
	    return ans
	    
    def solve(self,arr,n,dp):
        
        if n==0: return arr[0]
        
        if n<0: return 0
        
        if dp[n]!= -1:
            return dp[n]
        
        include = self.solve(arr,n-2,dp)+arr[n]
        exclude = self.solve(arr,n-1,dp)+ 0 
        
        dp[n] = max(include,exclude)
        
        return dp[n]

```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> space optimization
```Python
class Solution:
	
	def findMaxSum(self,arr, n):
	    
	    ans = self.solve(arr,n)
	    return ans
	    
    def solve(self,arr,n):
        prev1 = arr[0]
        prev2 = 0
	    
	    for i in range(1,n):
	        include = prev2 + arr[i]
	        exclude = prev1 + 0
	        ans = max(include,exclude)
	        
	        prev2 = prev1
	        prev1 = ans
	    
	    return prev1
```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[Max Sum without Adjacents](https://practice.geeksforgeeks.org/problems/max-sum-without-adjacents2430/1)
