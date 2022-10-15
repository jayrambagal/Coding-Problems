## String formation from substring
Given a string s, the task is to check if it can be constructed by taking 

a substring of it and appending multiple copies of the substring together. 

## Example 
```bash
Input: s = "ababab"
Output: 1
Explanation: It is contructed by 
appending "ab" 3 times

Input: s = "ababac"
Output: 0
Explanation: Not possible to construct
```


## Solution 

```python
class Solution:
	def isRepeat(self, s):
		n = len(s)
		lps = [0]*n # largest prefix and suffix
		i = 0
		j = 1
		
		while j<n:
		    
		    if s[i]==s[j]:
		        lps[j] = i+1
		        i+=1
		        j+=1
		        
		    else:
		        if i==0:
		            lps[j] = 0
		            j+=1
		        else:
		            i = lps[i-1]
		            
		if lps[n-1]==0:
		     
		     return 0
		   
		if n%(n-lps[n-1]) == 0 :    # klp algoritham
		    return 1
		else:
		    return 0

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## CodeChef
[String formation from substring](https://practice.geeksforgeeks.org/problems/string-formation-from-substring2734/1?page=2&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Strings&sortBy=submissions)
