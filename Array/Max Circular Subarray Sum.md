## Max Circular Subarray Sum
Given an array arr[] of N integers arranged in a circular fashion. 

Your task is to find the maximum contiguous subarray sum.

## Example 
```bash
Input:
N = 7
arr[] = {8,-8,9,-9,10,-11,12}
Output:
22
Explanation:
Starting from the last element
of the array, i.e, 12, and 
moving in a circular fashion, we 
have max subarray as 12, 8, -8, 9, 
-9, 10, which gives maximum sum 
as 22.

```

## Solution 

```python
def circularSubarraySum(arr,n):
    
    if n==1:
        return arr[0]
    max_sum = -1e9
    for i in range(n):
        k = i
        summ = arr[i]
        
        for j in range(i+1,n):
            summ+=arr[j]
            max_sum = max(max_sum,summ,arr[j])
    
            
        for l in range(i):
            summ+=arr[l]
            max_sum = max(max_sum,summ,arr[l])
            
    return max_sum
 ```
#### Complexity
```bash
Time Complexity :O(n*n)
Space Complexity : O(1)
```
## Solution 

```python
def circularSubarraySum(a,n):
    
    if (n == 1):
        return a[0]

    summ = sum(arr)
    curr_max = a[0]
    max_so_far = a[0]
    curr_min = a[0]
    min_so_far = a[0]
 
    for i in range(1, n):
       
        curr_max = max(curr_max + a[i], a[i])
        max_so_far = max(max_so_far, curr_max)
 
        
        curr_min = min(curr_min + a[i], a[i])
        min_so_far = min(min_so_far, curr_min)
        
    if (min_so_far == summ):
        return max_so_far
 
    
    return max(max_so_far, summ - min_so_far)
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[Max Circular Subarray Sum](https://practice.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&category[]=Arrays&sortBy=submissions)
