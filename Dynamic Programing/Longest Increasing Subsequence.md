## Longest Increasing Subsequence

Given an array of integers, find the length of the longest (strictly) increasing subsequence from the given array.

## Example 1


```bash
Input:
N = 16
A[]={0,8,4,12,2,10,6,14,1,9,5
     13,3,11,7,15}
Output: 6
Explanation:Longest increasing subsequence
0 2 6 9 13 15, which has length 6
```
## Solution 1 (recursion) 
```Python
class Solution:
    def longestSubsequence(self,arr,n):
        return self.solve(arr,n,0,-1)
        
    def solve(self,arr,n,ind,prev_ind):
        
        if ind == n:
            return 0
        
        take = 0
        if prev_ind == -1 or arr[ind]>arr[prev_ind] :
            take = 1 + self.solve(arr,n,ind+1,ind)
            
        not_take = 0 + self.solve(arr,n,ind+1,prev_ind)
        
        return max(not_take,take)
        
```
#### Complexity
```bash
Time Complexity : Exponentioal
Space Complexity : greater than O(n)
```
## Solution (Memoiation)
```python
class Solution:

    def longestSubsequence(self,arr,n):
        
        dp = [[-1 for i in range(n+1)]for j in range(n)]
        return self.solve(arr,n,0,-1,dp)
        
    def solve(self,arr,n,ind,prev_ind,dp):
        
        if ind == n:
            return 0
        
        if dp[ind][prev_ind+1] != -1:
            return dp[ind][prev_ind+1]
        
        take = 0
        if prev_ind == -1 or arr[ind]>arr[prev_ind] :
            take = 1 + self.solve(arr,n,ind+1,ind,dp)
            
        not_take = 0 + self.solve(arr,n,ind+1,prev_ind,dp)
        
        dp[ind][prev_ind+1] =  max(not_take,take)
        
        return dp[ind][prev_ind+1]
```

```bash
Time Complexity : O(n*n)
Space Complexity : O(n*n)+O(n)
```

## Solution (Tabulation)
```python

class Solution:
    
    #Function to find length of longest increasing subsequence.
    def longestSubsequence(self,a,n):
        
        dp = [0]*(n)
        
        max_ans = 0
        
        for i in range(n):
            ans = 0
            for j in range(0,i):
                if a[i]>a[j]:
                    ans = max(ans,dp[j])
            dp[i] = ans+1
            max_ans = max(dp[i],max_ans)
        return max_ans
            
```
	    
    

```bash
Time Complexity : O(n*n)
Space Complexity : O(n)
```
## GeeksForgeeks
[Longest Increasing Subsequence](https://practice.geeksforgeeks.org/problems/longest-increasing-subsequence-1587115620/1?page=1&difficulty[]=0&difficulty[]=1&status[]=unsolved&category[]=Dynamic%20Programming&sortBy=submissions)
