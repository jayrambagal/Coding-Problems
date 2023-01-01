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
      
       maxi = [s]
       string = [char for char in s]
       idx = 0

       self.findMaxNumUtil(string, k, idx, maxi)
       
       return maxi[0]
   
   def findMaxNumUtil(self, string, k, idx, maxi):
       if k <= 0 or idx >= len(string)-1:
           return
       # Find maximum for idx+1 to n
       max_in_str = string[idx]
       for m in range(idx+1, len(string)):
           if int(string[m]) > int(max_in_str):
               max_in_str = string[m]
       
       if string[idx] != max_in_str:
           k -= 1

       # swap idx with max_in_str and recursively find maximum
       for i in range(idx, len(string)):
           if string[i] == max_in_str:
               string[idx], string[i] = string[i], string[idx]
               
               new_str = "".join(string)
               if int(new_str) > int(maxi[0]):
                   maxi[0] = new_str
               
               # recur for chars idx+1 to n
               self.findMaxNumUtil(string, k, idx+1, maxi)
               
               # backtrack
               string[idx], string[i] = string[i], string[idx]
```
### Complexity
 
```bash
Time Complexity : 
Space Complexity : 
```

## Geeksforgeeks
[Largest number in K swaps](https://practice.geeksforgeeks.org/problems/largest-number-in-k-swaps-1587115620/1?page=1&status[]=unsolved&category[]=Recursion&category[]=Backtracking&sortBy=submissions)
