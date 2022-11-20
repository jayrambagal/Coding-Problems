## Longest valid Parentheses

Given a string S consisting of opening and closing parenthesis '(' and ')'. Find length of the longest valid parenthesis substring.

A parenthesis string is valid if:

For every opening parenthesis, there is a closing parenthesis.
Opening parenthesis must be closed in the correct order.

#### Example
```bash
Input: S = )()())
Output: 4
Explaination: The longest valid 
parenthesis substring is "()()".

```
### Solution 

```python
class Solution:
    def maxLength(self, S):
        
        stack = [-1]
        ans = 0
        
        for i in range(len(S)):
            if S[i]=="(":
                stack.append(i)
            else:
                stack.pop()
                
                if len(stack)==0:
                    stack.append(i)
                else:
                    ans = max(ans,i-stack[-1])
        return ans
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n) 
```

## Leetcode       
[Longest valid Parentheses](https://practice.geeksforgeeks.org/problems/longest-valid-parentheses5657/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Stack&category[]=Queue&category[]=two-pointer-algorithm&category[]=sliding-window&sortBy=submissions)
