## Rotate a 2D array without using extra space
Given a N x N 2D matrix Arr representing an image. Rotate the image by 90 degrees (anti-clockwise). 
You need to do this in place. Note that if you end up using an additional array, you will only receive partial score.

## Example 
```bash
Input:
N = 3
Arr[][] = {{1,  2,  3}
           {4,  5,  6}
           {7,  8,  9}}
Output:
 3  6  9 
 2  5  8 
 1  4  7 
Explanation: The given matrix is rotated
by 90 degree in anti-clockwise direction.

```
## Approach 
 
 first find the transpose of matrix 
 and then reverse array column wise
 

## Solution

```python

class Solution:
    
    def rotateMatrix(self,arr, n):
        
        
        for i in range(n):
            for j in range(i+1,n):
                
                arr[i][j],arr[j][i] = arr[j][i],arr[i][j]
        C = n        
        for i in range(C):
            j = 0
            k = C-1
            while j < k:
                t = arr[j][i]
                arr[j][i] = arr[k][i]
                arr[k][i] = t
                j += 1
                k -= 1
                
        return arr
```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity : O(1)

```

## Geeksforgeeks
[Rotate a 2D array without using extra space](https://practice.geeksforgeeks.org/problems/rotate-a-2d-array-without-using-extra-space1004/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Google&category[]=Arrays&sortBy=submissions)
