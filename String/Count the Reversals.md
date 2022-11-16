## Count the Reversals
Given a string S consisting of only opening and closing curly brackets '{' and '}', find out the minimum number 

of reversals required to convert the string into a balanced expression.

A reversal means changing '{' to '}' or vice-versa.

## Example 
```bash
Input:
S = "}{{}}{{{"
Output: 3
Explanation: One way to balance is:
"{{{}}{}}". There is no balanced sequence
that can be formed in lesser reversals.
```


## Solution 

```python
def countRev (s):
    temp = 0
    ans = 0
    
    if (len(s)%2 !=0):
        return -1
    
    for i in range(len(s)):
        if s[i] == "{":
            temp+=1
        else:
            if temp ==0:
                ans+=1
                temp+=1
            else:
                temp-=1
    
    if temp>0:
        ans += temp//2
        
    return ans

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

## Geeksforgeeks
[Count the Reversals](https://practice.geeksforgeeks.org/problems/count-the-reversals0401/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Strings&sortBy=submissions)
