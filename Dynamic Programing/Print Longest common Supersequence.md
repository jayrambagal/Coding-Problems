## Print Shortest Common Supersequence

## Example
```bash
Input:
X = "brute"
Y = "groot"

Output: bgruoote



```
### Approach
finding length of supersequence
ans = (n+m) - lcs

## Solution 1 

```Python

def shortestSupersequence(X: str, Y: str) -> str:
    m = len(X)
    n = len(Y)
    L = [[0 for i in range(n+1)] for j in range(m+1)]
    for i in range(m+1):
        for j in range(n+1):
            if i == 0 or j == 0:
                L[i][j] = 0
            elif X[i-1] == Y[j-1]:
                L[i][j] = L[i-1][j-1] + 1
            else:
                L[i][j] = max(L[i-1][j], L[i][j-1])
    lcs = ""
    i = m
    j = n
    while i > 0 and j > 0:
        if X[i-1] == Y[j-1]:
            lcs += X[i-1]
            i -= 1
            j -= 1
        elif L[i-1][j] > L[i][j-1]:
            lcs+=X[i-1]
            i -= 1
        else:
            lcs+=Y[j-1]
            j -= 1
            
    while i>0:
        lcs+=X[i-1]
        i-=1
    while j>0:
        lcs+=Y[j-1]
        j-=1
        
    lcs = lcs[::-1]
    return lcs
         
         
        
```
### Complexity
 
```bash
Time Complexity : O(n*m)
Space Complexity : O(n*m)
```



## Coading Ninjas
[Shortest Common Supersequence](https://www.codingninjas.com/codestudio/problems/shortest-supersequence_4244493?source=youtube&campaign=striver_dp_videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_dp_videos&leftPanelTab=0)
