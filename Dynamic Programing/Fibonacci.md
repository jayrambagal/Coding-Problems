
## Template

Given an array Arr[] of N integers. Find the contiguous sub-array(containing at least one number) which has the maximum sum and return its sum.
## Example 1


```bash
Input:
N = 5
Arr[] = {1,2,3,-2,5}
Output:
9
Explanation:
Max subarray sum is 9
of elements (1, 2, 3, -2, 5) which 
is a contiguous subarray.
```

## Solution 1

```Python

def maxSubArraySum(self,arr,N):
        
        count=0
        max_count=-999999999
        
        for i in range(0,N):
            count = count+arr[i]
            
            if max_count<count:
                max_count=count
                
            if count<0:
                count=0
                
        return max_count

```



## Geeksforgeeks
[Kadane's Algorithm ](https://practice.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1/?page=1&difficulty[]=1&category[]=Arrays&sortBy=submissions)

### Complexity
 
```bash
Time Complexity : O(n)
Space Complexity : O(1)


![Logo](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/th5xamgrr6se0x5ro4g6.png)

