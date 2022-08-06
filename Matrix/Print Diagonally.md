## Print Diagonally
Give a N * N square matrix, return all the elements of its anti-diagonals from top to bottom.

## Example 
```bash
Input: 
N = 2
A = [[1, 2],
     [3, 4]]
Output:
1 2 3 4

Input: 
N = 3 
A = [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]
Output: 
1 2 4 3 5 7 6 8 9


```
## Solution

```python

def downwardDigonal(n, A): 
    ans = []
    
    for i in range(n):
        row = 0
        col = i
        while (col>=0):
            ans.append(A[row][col])
            row+=1
            col-=1
    for i in range(1,n):
        row = i
        col = n-1
        
        while(row<n):
            ans.append(A[row][col])
            row+=1
            col-=1
            
    return ans
```



