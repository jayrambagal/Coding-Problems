## Count ways to reach the n'th stair
There are n stairs, a person standing at the bottom wants to reach the top. The person can climb either 1 stair or 2 stairs at a time. Count the number of ways, the person can reach the top (order does matter).
## Example 1


```bash
n = 4
Output: 5
Explanation:
You can reach 4th stair in 5 ways. 
Way 1: Climb 2 stairs at a time. 
Way 2: Climb 1 stair at a time.
Way 3: Climb 2 stairs, then 1 stair
and then 1 stair.
Way 4: Climb 1 stair, then 2 stairs
then 1 stair.
Way 5: Climb 1 stair, then 1 stair and
then 2 stairs.
Output: 5

```

## Solution 1 (Recursion)

```Python

    def countWays(self,n):
        if (n<0):
            return 0
        if (n==0):
            return 1
        ans = self.countWays(n-1)+self.countWays(n-2)
        return ans

```
### Complexity
 
```bash
Time Complexity : O(n^2)
Space Complexity : O(n)
```

## Geeksforgeeks
[Count ways to reach the n'th stair](https://practice.geeksforgeeks.org/problems/count-ways-to-reach-the-nth-stair-1587115620/1)
