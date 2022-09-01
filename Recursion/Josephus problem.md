## Josephus problem
```
Given the total number of persons n and a number k which indicates that k-1 persons 
are skipped and kth person is killed in circle in a fixed direction.

The task is to choose the safe place in the circle so that when you perform these operations 
starting from 1st place in the circle, you are the last one remaining and survive.
```
## Example 1


```bash
Input:
n = 3 k = 2
Output: 3
Explanation: There are 3 persons so 
skipping 1 person i.e 1st person 2nd 
person will be killed. Thus the safe 
position is 3.

```

## Solution 1 (Recursion)

```Python

class Solution:
    def josephus(self,n,k):
        
        arr = []
        
        for i in range(1,n+1):
            arr.append(i)
            
        self.solve(0,k,arr)
        return arr[0]
        
    def solve(self,i,k,arr):
        if len(arr)==1:
            return
        i = (i+k-1)%len(arr)
        arr.remove(arr[i])
        self.solve(i,k,arr)
```
### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Josephus problem](https://practice.geeksforgeeks.org/problems/josephus-problem/1?page=1&difficulty[]=0&company[]=Amazon&company[]=Microsoft&company[]=Flipkart&company[]=Adobe&company[]=Google&company[]=Goldman%20Sachs&category[]=Bit%20Magic&sortBy=submissions)
