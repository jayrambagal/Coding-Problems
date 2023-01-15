## Boolean Parenthesization
```
Given a boolean expression S of length N with following symbols.
Symbols
    'T' ---> true
    'F' ---> false
and following operators filled between symbols
Operators
    &   ---> boolean AND
    |   ---> boolean OR
    ^   ---> boolean XOR
Count the number of ways we can parenthesize the expression so that the value of expression evaluates to true.
```

#### Example
```bash

Input: N = 7
S = T|T&F^T
Output: 4
Explaination: The expression evaluates 
to true in 4 ways ((T|T)&(F^T)), 
(T|(T&(F^T))), (((T|T)&F)^T) and (T|((T&F)^T)).

```
### Solution 

```python
class Solution:
    def countWays(self, N, S):
        mod = 1003
        boolean,operaters = "" , ""
        
        # Separrate the string i'll separate the true & false string in boolean
        for i in S:
            if i=="T" or i=="F":
                boolean+=i
            else:
                operaters+=i
        n = len(boolean)
        
        # making the dp arrays for storing the dpTrue and DpFalse
        dpt = [[0 for i in range(n)] for j in range(n)]
        dpf = [[0 for j in range(n)] for i in range(n)]
        
        for g in range(n):
            i=0
            j=g
            while j<n and i<n:
                
                if g==0:
                    if boolean[i] == "T":
                        dpt[i][j] = 1
                        dpf[i][j] = 0
                        
                    elif boolean[i]=="F":
                        dpt[i][j] = 0
                        dpf[i][j] = 1
                        
                else:
                    for k in range(i,j):
                        
                        lTc = dpt[i][k]
                        rTc = dpt[k+1][j]
                        lFc = dpf[i][k]
                        rFc = dpf[k+1][j]
                        
                        if operaters[k] == "&":
                            dpt[i][j]+= lTc*rTc
                            dpf[i][j]+= (lTc*rFc + lFc*rTc + lFc*rFc)
                            
                        elif operaters[k] == "|":
                            dpt[i][j]+= (lTc*rTc + lTc*rFc + rTc*lFc)
                            dpf[i][j]+= lFc*rFc
                            
                        elif operaters[k] == "^":
                            dpt[i][j]+= (lTc*rFc + lFc*rTc)
                            dpf[i][j]+= (lTc*rTc + lFc*rFc)
                        
                i+=1
                j+=1
                
        return dpt[0][-1]%mod
       
        
```
### Complexity
```bash
Time Complexity = O()
Space Complexity = O()
```


[Boolean Parenthesization](https://practice.geeksforgeeks.org/problems/boolean-parenthesization5610/1)
