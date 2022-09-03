## Minimum time to fulfil all orders
```
Geek is organizing a party at his house. For the party, he needs exactly N donuts for the guests. 
Geek decides to order the donuts from a nearby restaurant, which has L chefs and each chef has a rank R. 
A chef with rank R can make 1 donut in the first R minutes, 1 more donut in the next 2R minutes, 1 more donut in 3R minutes, and so on.
For example. a chef with rank 2, can make one donut in 2 minutes, one more donut in the next 4 minutes, and one 
more in the next 6 minutes. So, it take 2 + 4 + 6 = 12 minutes to make 3 donuts. A chef can move on to making the 
next donut only after completing the previous one. All the chefs can work simultaneously.
Since, it's time for the party, Geek wants to know the minimum time required in completing N donuts. Return an integer denoting the minimum time
```

## Example 
```bash
Input:
N = 10
L = 4
rank[] = {1, 2, 3, 4}
Output: 12
Explanation: 
Chef with rank 1, can make 4 donuts in time 1 + 2 + 3 + 4 = 10 mins
Chef with rank 2, can make 3 donuts in time 2 + 4 + 6 = 12 mins
Chef with rank 3, can make 2 donuts in time 3 + 6 = 9 mins
Chef with rank 4, can make 1 donuts in time = 4 minutes
Total donuts = 4 + 3 + 2 + 1 = 10 and total time = 12 minutes.


Input:
N = 8
L = 8
rank[] = {1, 1, 1, 1, 1, 1, 1, 1}
Output: 1
Explanation: 
As all chefs are ranked 1, so each chef can make 1 donuts 1 min.
Total donuts = 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 = 8 and total time = 8 minutes. 

```

## Solution 

```python
from typing import List
class Solution:
   def findMinTime(self, n : int, l : int, arr : List[int]) -> int:
      
       ans=[]
       for x in arr:
           ele=x
           ans.append(x)
           for i in range(2,n+1):
               ans.append(ans[-1]+(ele*i))
               #keep the count of
               #total time req to bake by one chef
               #sort
       ans.sort()
       
       return ans[n-1] 
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```

 

## Geeksforgeeks
[Minimum time to fulfil all orders](https://practice.geeksforgeeks.org/problems/minimum-time-to-fulfil-all-orders/1)
