## Generate Parentheses

Given an integer N representing the number of pairs of parentheses, the task 

is to generate all combinations of well-formed(balanced) parentheses.

#### Example
```bash
Input:
N = 3
Output:
((()))
(()())
(())()
()(())
()()()
```
### Solution 

```python
class Solution:
    def AllParenthesis(self,n):
        ans=[]
        
        def solve(op,cp,output):
            
            if op==n and cp==n:
                ans.append(output[::])
                return
            if op<n:
                solve(op+1,cp,output+"(")
            if cp<op:
                solve(op,cp+1,output+")")
        solve(0,0,"")
                
        return ans
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n)
```
        
[Generate Parenthesest](https://practice.geeksforgeeks.org/problems/generate-all-possible-parentheses/1)
