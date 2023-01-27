## Total Decoding Messages

A top secret message containing letters from A-Z is being encoded to numbers using the following mapping:

'A' -> 1
'B' -> 2
...
'Z' -> 26

You are an FBI agent. You have to determine the total number of ways that message can be decoded, 

as the answer can be large return the answer modulo 109 + 7.

Note: An empty digit sequence is considered to have one decoding. It may be assumed that the input contains valid digits from 0 to 9 and 

If there are leading 0s, extra trailing 0s and two or more consecutive 0s then it is an invalid string.

#### Example
```bash
Input: str = "123"
Output: 3
Explanation: "123" can be decoded as "ABC"(123),
"LC"(12 3) and "AW"(1 23).

Input: str = "90"
Output: 0
Explanation: "90" cannot be decoded as it's an invalid string and we cannot decode '0'.
```

### Solution 

```python
class Solution:
	def CountWays(self, s):
	    
	    mod = 1000000007
	    n = len(s)
	    dp = [0]*n
	    dp[0] = 1
	    check = ""
	    
	    for i in range(1,n):
          
          # both are 00
	        if s[i]=='0' and s[i-1]=='0':
	            dp[i]=0
	         # 0 and non-zero conditon   
	        elif s[i]=='0' and s[i-1]!='0':
	            if s[i-1] == '1' or s[i-1]=='2':
	                if i>=1:
	                    dp[i] = dp[i-2]
	                else:
	                    dp[i]=1
	            else:
	                dp[i] = 0
	        # for non-zero and 0 condition        
	        elif s[i]!='0' and s[i-1]=='0':
	            dp[i] = dp[i-1]
          # for both non-zero condition
	        else:
	            check = s[i-1]+s[i]
	            
	            if int(check)<=26:
	                if i>1:
	                    dp[i] = dp[i-1]+dp[i-2]
	                else:
	                    dp[i] = dp[i-1]+1
	            else:
	                dp[i] = dp[i-1]
	    
	    return dp[n-1]%mod
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n)
```


[Total Decoding Messages](https://practice.geeksforgeeks.org/problems/total-decoding-messages1235/1)
