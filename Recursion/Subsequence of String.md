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

## Solution 

```python

def subsequences(str):
    n = len(str)
    ans = []
    temp = ""
    subsequencesHelper(str, 0, temp, ans)
    return ans

def subsequencesHelper(s, index, temp, ans):

    if(index == len(s)):
        if(len(temp) != 0):
            ans.append(temp)
        return
    subsequencesHelper(s, index + 1, temp, ans)
    temp += s[index]
    subsequencesHelper(s, index + 1, temp, ans)
```




