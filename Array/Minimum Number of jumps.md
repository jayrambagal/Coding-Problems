## Minimum Number of Jumps

Given an array of N integers arr[] where each element represents the max length of the jump that can be made forward from that element. Find the minimum number of jumps to reach the end of the array (starting from the first element). If an element is 0, then you cannot move through that element.

Note: Return -1 if you can't reach the end of the array.

## Example 
```bash
Input:
N = 11 
arr[] = {1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9} 
Output: 3 
Explanation: 
First jump from 1st element to 2nd 
element with value 3. Now, from here 
we jump to 5th element with value 9, 
and from here we will jump to the last. 

Input :
N = 6
arr = {1, 4, 3, 2, 6, 7}
Output: 2
```
## Solution

```python
class Solution:
    def minJumps(self, arr, n):
        
        if len(arr) <= 1 : 
            return 0 
   
        if arr[0] == 0 :  
            return -1 
  
        maxReach = arr[0]; 
        step = arr[0]; 
        jump = 1; 
        
        for i in range(1,len(arr)):
            if  i == len(arr) - 1 : 
                return jump 
                
            maxReach = max(maxReach, i+arr[i])
            step-=1; 
            
            if  step == 0 : 
                jump+=1  
                
                if i>=maxReach : 
                   return -1
                   
                step = maxReach - i 
  
        return -1  
```



