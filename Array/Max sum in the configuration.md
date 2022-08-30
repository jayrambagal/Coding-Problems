## Max sum in the configuration
Given an array(0-based indexing), you have to find the max sum of i*A[i] where A[i] 

is the element at index i in the array. The only operation allowed is to rotate(clock-wise or counter clock-wise) 

the array any number of times.

## Example 
```bash
Input:
N = 4
A[] = {8,3,1,2}
Output: 29
Explanation: Above the configuration
possible by rotating elements are
3 1 2 8 here sum is 3*0+1*1+2*2+8*3 = 29
1 2 8 3 here sum is 1*0+2*1+8*2+3*3 = 27
2 8 3 1 here sum is 2*0+8*1+3*2+1*3 = 17
8 3 1 2 here sum is 8*0+3*1+1*2+2*3 = 11
Here the max sum is 29 

```

## Solution 

```python
def max_sum(a,n):
    count = 0
    res = 0

    while count < n:
        ans = 0
        for i in range(n):
            ans += a[i] * i
        res = max(res, ans)
        ele = a[0]
        a.pop(0)
        count+=1
        a.append(ele)
        
    return res
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```

## Geeksforgeeks
[Max sum in the configuration](https://practice.geeksforgeeks.org/problems/max-sum-in-the-configuration/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&sortBy=submissions)
