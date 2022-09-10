## Distribute N candies among K people
```
Given N candies and K people. In the first turn, the first person gets 1 candy, 
the second gets 2 candies, and so on till K people. In the next turn, the first 
person gets K+1 candies, the second person gets K+2 candies and so on. If the 
number of candies is less than the required number of candies at every turn, 
then the person receives the remaining number of candies. Find the total number 
of candies every person has at the end.
```

## Example 
```bash
Input:
N = 7, K = 4
Output:
1 2 3 1
Explanation:
At the first turn, the fourth person
has to be given 4 candies, but there is
only 1 left, hence he takes only one. 

```

## Solution (optimized)

```python
class Solution:
    def distributeCandies(self, N, K):
        
        ans = [0]*K
        x = 0
        while N>0:
            ans[x%K] += min(x+1,N)
            x+=1
            N-= x
        return ans

```
#### Complexity
```bash
Time Complexity :O(sqrt(n))
Space Complexity : O(1)

```

## LeetCode
[Distribute N candies among K people](https://practice.geeksforgeeks.org/problems/distribute-n-candies/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Binary%20Search&sortBy=submissions)
