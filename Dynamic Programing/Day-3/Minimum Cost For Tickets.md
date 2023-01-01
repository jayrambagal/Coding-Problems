## Minimum Cost For Tickets
You have planned some train traveling one year in advance. The days of the year in which you will travel are given as an integer array days. 

Each day is an integer from 1 to 365.

Train tickets are sold in three different ways:

a 1-day pass is sold for costs[0] dollars,
a 7-day pass is sold for costs[1] dollars, and
a 30-day pass is sold for costs[2] dollars.
The passes allow that many days of consecutive travel.

For example, if we get a 7-day pass on day 2, then we can travel for 7 days: 2, 3, 4, 5, 6, 7, and 8.
Return the minimum number of dollars you need to travel every day in the given list of days.
## Example 1


```bash
Input: days = [1,4,6,7,8,20], costs = [2,7,15]
Output: 11
Explanation: For example, here is one way to buy passes that lets you travel your travel plan:
On day 1, you bought a 1-day pass for costs[0] = $2, which covered day 1.
On day 3, you bought a 7-day pass for costs[1] = $7, which covered days 3, 4, ..., 9.
On day 20, you bought a 1-day pass for costs[0] = $2, which covered day 20.
In total, you spent $11 and covered all the days of your travel.

```

## Solution 1 (Recursion)

```Python

class Solution:
    def find(self, days, i, target):
        while i < len(days) and days[i] <= target:
            i = i+1
        return i
    
    def solve(self, days, costs, i):
        if i >= len(days):
            return 0
        x1 = self.solve(days, costs, i+1) + costs[0]
        index = self.find(days, i, days[i]+6)
        x2 = self.solve(days, costs, index) + costs[1]
        index = self.find(days, i, days[i]+29)
        x3 = self.solve(days, costs, index) + costs[2]
        return min(x1, x2, x3)
    
    def mincostTickets(self, days: List[int], costs: List[int]) -> int:
        return self.solve(days, costs, 0)
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
class Solution:
    def find(self, days, i, target):
        while i < len(days) and days[i] <= target:
            i = i+1
        return i
    
    def solve(self, days, costs, i, d):
        if i >= len(days):
            return 0
        if i in d:
            return d[i]
        x1 = self.solve(days, costs, i+1, d) + costs[0]
        index = self.find(days, i, days[i]+6)
        x2 = self.solve(days, costs, index, d) + costs[1]
        index = self.find(days, i, days[i]+29)
        x3 = self.solve(days, costs, index, d) + costs[2]
        d[i] = min(x1, x2, x3)
        return d[i]
    
    def mincostTickets(self, days: List[int], costs: List[int]) -> int:
        return self.solve(days, costs, 0, {})
```
### Complexity
 

```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```

## GeeksforGeeks
[Minimum Cost For Tickets](https://leetcode.com/problems/minimum-cost-for-tickets/description/)
