## Consecutive 1's not allowed
Given a positive integer N, count all possible distinct binary strings of 

length N such that there are no consecutive 1’s. Output your answer modulo 10^9 + 7.

## Example 
```bash
Input:
N = 3
Output: 5
Explanation: 5 strings are (000,
001, 010, 100, 101).

```

## Solution 

```python
class Solution:

	def countStrings(self,n):
	    
	    a = [0 for i in range(n)]
	    b = [0 for j in range(n)]
	    a[0]=b[0] = 1
	    
	    for i in range(1,n):
	        a[i] = a[i-1]+b[i-1]
	        b[i] = a[i-1]
	        
	    return (a[n-1]+b[n-1])%1000000007
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[Consecutive 1's not allowed](https://practice.geeksforgeeks.org/problems/consecutive-1s-not-allowed1912/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Arrays&sortBy=submissions)
