## Handshakes

We have N persons sitting on a round table. Any person can do a handshake with any other person.

     1
2         3
     4

Handshake with 2-3 and 1-4 will cause cross.

In how many ways these N people can make handshakes so that no two handshakes cross each other. N would be even. 


 
## Example 1


```bash
Input:
N = 2
Output:
1
Explanation:
{1,2} handshake is
possible.

Input:
N = 4
Output:
2
Explanation:
{{1, 2}, {3, 4}} are the
two handshakes possible.
{{1, 3}, {2, 4}} is another
set of handshakes possible.
```

## Solution 
```python
class Solution:
    def count(self, N):
        
        dp = [0]*(N+1)
        dp[0] = 1
        
        for i in range(2,N+1,2):
            for j in range(0,i-1,2):
                dp[i]+=dp[j]*dp[i-2-j]
        return dp[N]
```
	    
    

```bash
Time Complexity : O(n)
Space Complexity : O(n)
```
## Leetcode
[Handshakes](https://practice.geeksforgeeks.org/problems/handshakes1303/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Recursion&category[]=Backtracking&sortBy=submissions)
