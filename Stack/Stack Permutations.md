## Stack Permutations
```
You are given two arrays A and B of unique elements of size N. Check if one array is a 
stack permutation of the other array or not.Stack permutation means that one array can 
be created from another array using a stack and stack operations.
```

#### Example
```bash
Input:
N = 3
A = {1,2,3}
B = {2,1,3}
Output:
1
Explanation:
1. push 1 from A to stack
2. push 2 from A to stack
3. pop 2 from stack to B
4. pop 1 from stack to B
5. push 3 from A to stack
6. pop 3 from stack to B

```
### Solution 

```python
class Solution:
    def isStackPermutation(self, N : int, A : List[int], B : List[int]) -> int:
        
        stack = []
        i = 0
        j = 0
        while j<N:
            while(i<N and (stack == [] or stack[-1]!=B[j])):
                stack.append(A[i])
                i+=1
                
            while(stack!=[] and stack[-1]==B[j]):
                stack.pop()
                j+=1
                
            if i==N and stack!=[] and stack[-1]!=B[j]:
                return 0
                
        return 1
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n) 
```        


## Leetcode       
[Stack Permutations](https://practice.geeksforgeeks.org/problems/stack-permutations/1)
