## Largest number in K swaps
Given a number K and string str of digits denoting a positive integer, build the largest number possible by performing 

swap operations on the digits of str at most K times.

## Example 1


```bash
Input:
K = 4
str = "1234567"
Output:
7654321
Explanation:
Three swaps can make the
input 1234567 to 7654321, swapping 1
with 7, 2 with 6 and finally 3 with 5

Input:
K = 3
str = "3435335"
Output:
5543333
Explanation:
Three swaps can make the input
3435335 to 5543333, swapping 3 
with 5, 4 with 5 and finally 3 with 4 
```


## Solution 2 (optimization)

```Python

class Solution:
   
    def findMaximumNum(self,s,k):
        maxm = [s]
        ans = self.solve(s,k,maxm)
        return ans
        
    def solve(self,string, k, maxm):
        if k == 0:
            return
        n = len(string)
     
        for i in range(n - 1):
            for j in range(i + 1, n):
     
                if string[i] < string[j]:
                    string = self.swap(string, i, j)
                    if string > maxm[0]:
                        maxm[0] = string
                    self.solve(string, k - 1, maxm)
                    string = self.swap(string, i, j)
        return maxm[0]
        
    def swap(self,s,i,j):
           strr = ""
           left = s[0:i]
           right = s[j+1:len(s)]
           mid = s[i+1:j]
           strr = left+s[j]+mid+s[i]+right
           return strr
```
### Complexity
 
```bash
Time Complexity : 
Space Complexity : 
```

## Geeksforgeeks
[Largest number in K swaps](https://practice.geeksforgeeks.org/problems/largest-number-in-k-swaps-1587115620/1?page=1&status[]=unsolved&category[]=Recursion&category[]=Backtracking&sortBy=submissions)
