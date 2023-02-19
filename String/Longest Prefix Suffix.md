## Longest Prefix Suffix
Given a string of characters, find the length of the longest proper prefix which is also a proper suffix.

NOTE: Prefix and suffix can be overlapping but they should not be equal to the entire string.

## Example 
```bash
Input: s = "abab"
Output: 2
Explanation: "ab" is the longest proper 
prefix and suffix. 

Input: s = "aaaa"
Output: 3
Explanation: "aaa" is the longest proper 
prefix and suffix.


```
### explanation
```
proper prifix == 0 to n-1 (n-1,n-2 anything) ---> not including nth position
proper suffix means == 1 or 2... to  Nth position ---> not included 0th pos

example:

s = "abcde"

proper prifix -->
a
ab
abc
abcd

proper suffix -->
bcde
cde
de
e
```

## Solution (brut force)

```python
class Solution:
	def lps(self, s):
	    
		pre = ""
		suf = ""
		ans = 0
		n = len(s)
		
		for i in range(n-1):
		    pre+=s[i]
		    suf = s[n-i-1] + suf
		    
		    if pre==suf:
		        ans = len(pre)
		        
		return ans
```

## Solution 

```python
class Solution:
	def lps(self, s):
	    
	    n = len(s)
	    lps = [0]*n
	    lps[0]=0
	    i = 0
	    j = 1
	    
	    while j<n:
	        
	        if s[i]==s[j]:
	            lps[j] = i+1
	            j+=1
	            i+=1
	        else:
	            if i==0:
	                lps[j] = 0
	                j+=1
	            else:
	                i = lps[i-1]
	    return lps[n-1]

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Longest Prefix Suffix](https://practice.geeksforgeeks.org/problems/longest-prefix-suffix2527/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Flipkart&company[]=Adobe&company[]=Google&company[]=Accolite&company[]=Snapdeal%20&company[]=Paytm&company[]=Goldman%20Sachs&company[]=OYO%20Rooms&category[]=Strings&sortBy=submissions)
