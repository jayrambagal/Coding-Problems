## Edite Distance
Given two strings s and t. Return the minimum number of operations required to convert s to t.
The possible operations are permitted:
```
1. Insert a character at any position of the string.
2. Remove any character from the string.
3. Replace any character from the string with any other character.
```
## Example
```bash
Input: 
s = "geek", t = "gesek"
Output: 1
Explanation: One operation is required 
inserting 's' between two 'e's of str1.

Input : 
s = "gfg", t = "gfg"
Output: 
0
Explanation: Both strings are same.
```

## Solution 1 (Recursion)

```Python

class Solution:
	def editDistance(self, s, t):
	    n = len(s)
	    m = len(t)
	    
	    return self.solve(n-1,m-1,s,t)
	    
	def solve(self,i,j,s,t):
	    
	    if i<0:
	        return j+1
	        
	    if j<0:
	        return i+1
	        
	        
	    if s[i]==t[j]:
	        return self.solve(i-1,j-1,s,t)
	        
	    else:
	        insert = self.solve(i,j-1,s,t)
	        delete = self.solve(i-1,j,s,t)
	        replace = self.solve(i-1,j-1,s,t)
	        
	        return 1+min(insert,delete,replace)
        
```
### Complexity
```bash
Time Complexity : Exponential
Space Complexity : O(n*m)
```

## Solution 2 --> Memoiation 

```Python
class Solution:
	def editDistance(self, s, t):
	    n = len(s)
	    m = len(t)
	    dp = [[-1 for _ in range(m+1)]for __ in range(n+1)]
	    
	    return self.solve(n-1,m-1,s,t,dp)
	    
	def solve(self,i,j,s,t,dp):
	    
	    if i<0:
	        return j+1
	        
	    if j<0:
	        return i+1
	   
	    if dp[i][j] != -1:
	        return dp[i][j]
	        
	    if s[i]==t[j]:
	        dp[i][j] = self.solve(i-1,j-1,s,t,dp)
	        return dp[i][j]
	        
	    else:
	        insert = self.solve(i,j-1,s,t,dp)
	        delete = self.solve(i-1,j,s,t,dp)
	        replace = self.solve(i-1,j-1,s,t,dp)
	        
	        dp[i][j] = 1+min(insert,delete,replace)
	        return dp[i][j]
          
 # changing base cases +1
 
 class Solution:
	def editDistance(self, s, t):
	    n = len(s)
	    m = len(t)
	    dp = [[-1 for _ in range(m+1)]for __ in range(n+1)]
	    
	    return self.solve(n,m,s,t,dp)    # n , m
	    
	def solve(self,i,j,s,t,dp):
	    
	    if i==0:                # ==0
	        return j
	        
	    if j==0:
	        return i
	   
	    if dp[i][j] != -1:
	        return dp[i][j]
	        
	    if s[i-1]==t[j-1]:            # i-1 , j-1
	        dp[i][j] = self.solve(i-1,j-1,s,t,dp)
	        return dp[i][j]
	        
	    else:
	        insert = self.solve(i,j-1,s,t,dp)
	        delete = self.solve(i-1,j,s,t,dp)
	        replace = self.solve(i-1,j-1,s,t,dp)
	        
	        dp[i][j] = 1+min(insert,delete,replace)
	        return dp[i][j]
        
```
### Complexity
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m) + O(n+m)
```
## Solution --> Tabulation
```python
class Solution:
	def editDistance(self, s, t):
	    n = len(s)
	    m = len(t)
	    INT_MAX=10000000
	    dp = [[INT_MAX for _ in range(m+1)]for __ in range(n+1)]
	    
	    for i in range(0,n):dp[i][0] = i
	    for j in range(0,m):dp[0][j] = j
	    
	    for i in range(1,n+1):
	        for j in range(1,m+1):
	            
	            if s[i-1]==t[j-1]:
	                dp[i][j] = dp[i-1][j-1] 
	                
	        
	            else:
	                insert =dp[i][j-1] 
	                delete =dp[i-1][j] 
	                replace =dp[i-1][j-1] 
	        
	                dp[i][j] = 1+min(insert,delete,replace)
	                
	    return dp[n][m]
```
### Complexity
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```


## GeeksforGeeks
[Edite Distance](https://practice.geeksforgeeks.org/problems/edit-distance3702/1)
