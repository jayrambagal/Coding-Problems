## Ransom Note
Given two strings ransomNote and magazine, return true if ransomNote can 

be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.


## Example 
```bash
Input: ransomNote = "aaa", magazine = "aab"
Output: false

Input: ransomNote = "aa", magazine = "aab"
Output: true

```


## Solution (Using Dict)
```python
class Solution:
    def canConstruct(self, str1: str, str2: str) -> bool:
        
        freq = dict()
        
        for i in str1:
            if i in freq:
                freq[i]+=1
                
            else:
                freq[i]=0
                
        for i in freq:
            if str2.count(i)<=freq[i]:
                return False
        return True
        
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## Leetcode
[Ransom Note](https://leetcode.com/problems/ransom-note/)
