## Generate IP Addresses
Given a string S containing only digits, Your task is to complete the function genIp() which returns a vector containing all possible combinations of valid IPv4 IP addresses and takes only a string S as its only argument.
Note: Order doesn't matter.

For string 11211 the IP address possible are 
1.1.2.11
1.1.21.1
1.12.1.1
11.2.1.1

## Example 
```bash
Input:
S = 1111
Output: 1.1.1.1

s ="1234556"

Output:

1.23.45.56
1.234.5.56
1.234.55.6
12.3.45.56
12.34.5.56
12.34.55.6
123.4.5.56
123.4.55.6
123.45.5.6

```

## Solution 

```python
class Solution:
    def genIp(self, s):
        n = len(s)
        if n<4 or n>12:  # valid ip is 0 to 255 --> x.x.x.x  len(x) == 3 0nly
            return [-1]
            
        ans = []
        
        for i in range(n-2):
            for j in range(i+1,n-1):
                for k in range(j+1,n):
                    
                    a = s[0:i]
                    b = s[i:j]
                    c = s[j:k]
                    d = s[k:n]
                    
                    if self.valid(a) and self.valid(b) and self.valid(c) and self.valid(d):
                        ans.append(a+"."+b+"."+c+"."+d)
        return ans
    
    def valid(self,s):
        n = len(s)
        
        if n==0 or n>3 or (s[0]=="0" and n>1) or int(s)>255:
            return False
        return True
        

```
#### Complexity
```bash
Time Complexity :O(n^3)
Space Complexity : O(1)

```

## Geeksforgeeks
[Generate IP Addresses](https://practice.geeksforgeeks.org/problems/generate-ip-addresses/1)
