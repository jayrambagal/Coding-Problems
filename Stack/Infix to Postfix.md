## Infix to Postfix
Given an infix expression in the form of string str. Convert this infix expression to postfix expression.

Infix expression: The expression of the form a op b. When an operator is in-between every pair of operands.

Postfix expression: The expression of the form a b op. When an operator is followed for every pair of operands.

Note: The order of precedence is: ^ greater than * equals to / greater than + equals to

#### Example
```bash
Input: str = "a+b*(c^d-e)^(f+g*h)-i"
Output: abcd^e-fgh*+^*+i-
Explanation:
After converting the infix expression 
into postfix expression, the resultant 
expression will be abcd^e-fgh*+^*+i-

```
### Solution 

```python
class Solution:

    def InfixtoPostfix(self, expression):
        Operators = set(['+', '-', '*', '/', '(', ')', '^']) 
        Priority = {'+':1, '-':1, '*':2, '/':2, '^':3}
        stack = [] 
        output = '' 

        for i in expression:
    
            if i not in Operators:  
                output+= i
                
            elif i=='(':  
                stack.append('(')
                
            elif i==')':
                while stack and stack[-1]!= '(':
                    output+=stack.pop()
                stack.pop()
                
            else: 
                while stack and stack[-1]!='(' and Priority[i]<=Priority[stack[-1]]:
                    output+=stack.pop()
                stack.append(i)

        while stack:
            output+=stack.pop()
    
        return output
        
```
### Complexity
```bash
Time Complexity = O(n^3)
Space Complexity = O(1) 
```

## Geeksforgeeks      
[Infix to Postfix](https://practice.geeksforgeeks.org/problems/infix-to-postfix-1587115620/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Stack&category[]=Queue&category[]=two-pointer-algorithm&category[]=sliding-window&sortBy=submissions)
