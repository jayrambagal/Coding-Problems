## Next Greater Element
```
Given an array arr[ ] of size N having distinct elements, the task is to find the 
next greater element for each element of the array in order of their appearance in the array.
Next greater element of an element in the array is the nearest element on the right which 
is greater than the current element.
If there does not exist next greater of current element, then next greater element for current 
element is -1. For example, next greater of the last element is always -1.
```

## Example 
```bash
Input: 
N = 4, arr[] = [1 3 2 4]
Output:
3 4 4 -1
Explanation:
In the array, the next larger element 
to 1 is 3 , 3 is 4 , 2 is 4 and for 4 ? 
since it doesn't exist, it is -1.

```

## Solution 

```python
class Solution:
    def nextLargerElement(self,arr,n):
        ans = [0]*n
        
        for i in range(n):
            for j in range(i+1,n):
                if arr[i]<arr[j]:
                    ans[i] = arr[j]
                    break
            if ans[i] == 0:
                ans[i] = -1
                
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```


## Solution
```python

 ```
 

## Geeksforgeeks
[Next Greater Element](https://practice.geeksforgeeks.org/problems/next-larger-element-1587115620/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Flipkart&company[]=Adobe&company[]=Google&company[]=Goldman%20Sachs&sortBy=submissions)
