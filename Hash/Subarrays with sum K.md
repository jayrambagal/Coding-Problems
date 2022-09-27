## Subarrays with sum K
Given an unsorted array of integers, find the number of continuous subarrays having sum exactly equal to a given number k.

## Example 
```bash
Input:
N = 5
Arr = {10 , 2, -2, -20, 10}
k = -10
Output: 3
Explaination: 
Subarrays: arr[0...3], arr[1...4], arr[3..4]
have sum exactly equal to -10.

```

 
## Solution
```python
class Solution:
    def findSubArraySum(self, Arr, N, k):
        mydict={0:1}
        sum1=0
        c=0
        for i in Arr:
            sum1+=i
            if sum1-k in mydict:
                c+=mydict[sum1-k]
            if sum1 in mydict:
                mydict[sum1]+=1
            else:
                mydict[sum1]=1
        return c

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Subarrays with sum K](https://practice.geeksforgeeks.org/problems/subarrays-with-sum-k/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Hash&sortBy=submissions)
