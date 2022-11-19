## Circular tour
Suppose there is a circle. There are N petrol pumps on that circle. You will be given two sets of data.

1. The amount of petrol that every petrol pump has.

3. Distance from that petrol pump to the next petrol pump.

Find a starting point where the truck can start to get through the complete circle without exhausting its petrol in between.

Note :  Assume for 1 litre petrol, the truck can go 1 unit of distance.

## Example 
```bash
Input:
N = 4
Petrol = 4 6 7 4
Distance = 6 5 3 5
Output: 1
Explanation: There are 4 petrol pumps with
amount of petrol and distance to next
petrol pump value pairs as {4, 6}, {6, 5},
{7, 3} and {4, 5}. The first point from
where truck can make a circular tour is
2nd petrol pump. Output in this case is 1
(index of 2nd petrol pump).
```


## Solution 

```python

class Solution:
    def tour(self,lis, n):
        recfule=0
        rem=0
        start=0

        for i in range(n):
            
            rem+=lis[i][0]-lis[i][1]
            
            if rem<0:
                start=i+1
                recfule+=rem
                rem=0
                
        if recfule+rem>=0:
            return start 
        else:
            return -1
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```


## Geeksforgeeks
[Circular tour](https://practice.geeksforgeeks.org/problems/circular-tour-1587115620/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=sliding-window&sortBy=submissions)
