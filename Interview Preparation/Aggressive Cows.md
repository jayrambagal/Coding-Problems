## Aggressive Cows
You are given an array consisting of n integers which denote the position of a stall. 

You are also given an integer k which denotes the number of aggressive cows. 

You are given the task of assigning stalls to k cows such that the minimum distance between any two of them is the maximum possible.

The first line of input contains two space-separated integers n and k.

The second line contains n space-separated integers denoting the position of the stalls.

## Example 
```bash
Input:
n=5 
k=3
stalls = [1 2 4 8 9]
Output:
3
Explanation:
The first cow can be placed at stalls[0], 
the second cow can be placed at stalls[2] and 
the third cow can be placed at stalls[3]. 
The minimum distance between cows, in this case, is 3, 
which also is the largest among all possible ways.

Input:
n=5 
k=3
stalls = [10 1 2 7 5]
Output:
4
Explanation:
The first cow can be placed at stalls[0],
the second cow can be placed at stalls[1] and
the third cow can be placed at stalls[4].
The minimum distance between cows, in this case, is 4,
which also is the largest among all possible ways.

```

## Solution 

```python
class Solution:
    def solve(self,n,k,stalls):
        stalls.sort()
        low = 0
        high = stalls[-1]
        
        while low <= high:
            mid = (low+high)//2
            
            if self.isPossible(stalls,k,mid):
                res = mid
                low = mid+1
            else:
                high = mid-1
        return res
                
    def isPossible(self,stalls,k,mid):
        count = 1
        lastCow = stalls[0]
        
        for i in range(1,len(stalls)):
            
            if stalls[i]-lastCow >= mid:
                count+=1
                lastCow = stalls[i]
                
                if count>= k:
                    return True
        return False
```
#### Complexity
```bash
Time Complexity :O()
Space Complexity : O()
```
## Geeksforgeeks
[Aggressive Cows](https://practice.geeksforgeeks.org/problems/aggressive-cows/1)
