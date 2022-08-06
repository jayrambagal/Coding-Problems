## 



## Example 
```bash

```
## Solution

```python
class Solution:
    #Function to rearrange an array so that arr[i] becomes arr[arr[i]]
    #with O(1) extra space.
    
    def arrange(self,arr, n): 
        
        nr = [0]*len(arr)

        for i in range(len(arr)):
            nr[i]=arr[arr[i]]
    
        for i in range(n):
            arr[i]=nr[i]
        return arr
             
```



