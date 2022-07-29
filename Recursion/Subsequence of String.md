## Subsequence of String 
You are given a string 'STR containing lowercase English letters from a to z inclusive. Your task is to find all non-empty possible
subsequences of 'STR'.
## Example 1


```bash
str ="abc"
output : a ab abc ac b bc c


```

## Solution 1 (Recursion)

```Python
def subsequences(str):

    return solve(str,0,[],"")
    
def solve(s,index,ans,out):
    
    if index>=len(s):
        ans.append(out)
        return 
    
    
    solve(s,index+1,ans,out)
    out+=s[index]
    solve(s,index+1,ans,out)
    
    return ans
    
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```




