## letter Combination of Phone Number
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
## Example 1


```bash
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]


```

## Solution 1 (Recursion)

```Python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        
        mapping = {'2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl', 
               '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz'}
        ans = []
    
        if digits == "":
            return []
        
        return self.solve(digits,mapping,ans,"",0)
    
    def solve(self,digits,mapping,ans,temp,index):
        if index >= len(digits):
            ans.append(temp)
            return
        val = mapping[digits[int(index)]]
        
        for i in range(len(val)):
            temp += val[i]
            self.solve(digits,mapping,ans,temp,index+1)
            temp = temp[:-1]
            
        
        return ans
    
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```



