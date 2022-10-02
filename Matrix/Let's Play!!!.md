## Let's Play!!!
Let's play a game!! Given a matrix mat[][] with n x m elements. Your task is to check that 

matrix is Super Similar or not. To perform this task you have to follow these Rules: Firstly 

all even index rows to be Rotated left and odd index rows to right, And Rotation is done X times(Index starting from zero). 

Secondly, After all the Rotations check if the initial and the final Matrix are same Return 1 else 0.

## Example 
```bash

Input: n = 2, m = 2
mat = {{1, 2}, 
       {5, 6}}
x = 1
Output: 0
Explanation: Matrix after rotation:
mat = {{ 2, 1}
       { 6, 5}}
After one rotation mat is 
not same as the previous one.

```
## Solution

```python

class Solution:
    def isSuperSimilar(self, n, m, mat, x):
        if(x%m==0):
            return 1;
        else:
            for i in range(n):
                for j in range(m):
                    if mat[i][j]!=mat[i][(j+x)%m]:
                        return 0
            return 1

```
## Complexity
```
Time Complexity : O(n^2) )
Space Complexity : O(1)
```


## Geeksforgeeks
[Let's Play!!!](https://practice.geeksforgeeks.org/problems/lets-play0201/1?page=4&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&category[]=Arrays&category[]=Strings&category[]=Hash&category[]=Sorting&category[]=Matrix&category[]=Searching&category[]=Stack&category[]=Recursion&category[]=Binary%20Search%20Tree&category[]=Binary%20Search&sortBy=submissions)
