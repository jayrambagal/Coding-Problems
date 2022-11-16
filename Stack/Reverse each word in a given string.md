## Reverse each word in a given string

Given a String. Reverse each word in it where the words are separated by dots.

#### Example
```bash
Input:
S = "i.like.this.program.very.much"
Output: 
i.ekil.siht.margorp.yrev.hcum
Explanation: 
The words are reversed as
follows:"i" -> "i","like"->"ekil",
"this"->"siht","program" -> "margorp",
"very" -> "yrev","much" -> "hcum".

``` 

### Solution 

```python
class Solution:
    def reverseWords(self, s):
        ans = ""
        stack = []
        for i in range(len(s)):
            
            if s[i]==".":
                
                while stack:
                    temp = stack.pop()
                    ans+=temp
                ans+="."
            else:
                stack.append(s[i])
                
        while stack:
            temp = stack.pop()
            ans+=temp
            
        return ans
        
```

## Geeksforgeeks      
[Reverse each word in a given string](https://practice.geeksforgeeks.org/problems/reverse-each-word-in-a-given-string1001/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Strings&sortBy=submissions)
