## Parenthesis Checker
Given an expression string x. Examine whether the pairs and the orders of “{“,”}”,”(“,”)”,”[“,”]” are correct in exp.

For example, the function should return 'true' for exp = “[()]{}{[()()]()}” and 'false' for exp = “[(])”.


## Example 
```bash
Input:
{([])}
Output: 
true
Explanation: 
{ ( [ ] ) }. Same colored brackets can form 
balaced pairs, with 0 number of 
unbalanced bracket.

```

## Solution 

```python

 def ispar(self,x):
        
        close = {')':'(','}':'{',']':'['}
        stack = []   
        
        for p in x:
            
            if p in close:
                if stack and stack[-1]==close[p]:
                    stack.pop()
                else:
                    return False
                    
            else:
                stack.append(p)
                
        if stack:
            return False
        else:
            return True
```


## Geeksforgeeks 
[Parenthesis Checker](https://practice.geeksforgeeks.org/problems/parenthesis-checker2744/1)
