## Rod Cutting
Given a rod of length N inches and an array of prices, price[]. pricei denotes the value of a piece of length i. 

Determine the maximum value obtainable by cutting up the rod and selling the pieces.

## Example 1


```bash
Input:
N = 8
Price[] = {1, 5, 8, 9, 10, 17, 17, 20}
Output:
22
Explanation:
The maximum obtainable value is 22 by
cutting in two pieces of lengths 2 and 
6, i.e., 5+17=22.

Input:
N=8
Price[] = {3, 5, 8, 9, 10, 17, 17, 20}
Output: 24
Explanation: 
The maximum obtainable value is 
24 by cutting the rod into 8 pieces 
of length 1, i.e, 8*3=24. 

```

## Solution 1 (Recursion)

```Python

 class Solution:
    def cutRod(self, price, n):
        
        
        def cutRod(price, index, n):

            if index == 0:
                return n*price[0]
           
            notCut = cutRod(price,index - 1,n)
            cut = float("-inf")
            rod_length = index + 1
         
            if (rod_length <= n):
                cut = price[index] + cutRod(price,index,n - rod_length)
           
            return max(notCut, cut)
 
        return cutRod(price,n-1,n)

```
### Complexity
 
```bash
Time Complexity : O(n^2)
Space Complexity : O(n)
```

## Solution 2 (memoiation)

```Python

class Solution:
    def cutRod(self, price, n):
        
        
        def cutRod(price, index, n,dp):

            if index == 0:
                return n*price[0]
                
            if dp[index][n] != -1:
                return dp[index][n]
           
            notCut = cutRod(price,index - 1,n,dp)
            cut = float("-inf")
            rod_length = index + 1
         
            if (rod_length <= n):
                cut = price[index] + cutRod(price,index,n - rod_length,dp)
           
            dp[index][n] = max(notCut, cut)
            
            return dp[index][n]
        
        dp = [[-1 for i in range(n+1)] for i in range(n+1)]
        return cutRod(price,n-1,n,dp)
```
### Complexity
 
```bash
Time Complexity : O()
Space Complexity : O()
```

## Geeksforgeeks
[Rod Cutting](https://practice.geeksforgeeks.org/problems/rod-cutting0840/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Recursion&category[]=Backtracking&sortBy=submissions)
