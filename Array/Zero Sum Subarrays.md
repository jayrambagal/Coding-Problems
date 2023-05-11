## Zero Sum Subarrays
You are given a array arr[] of size n. Find the total count of sub-arrays having their sum equal to 0.

## Example 
```bash
Input:
Input:
n = 6
arr[] = {0,0,5,5,0,0}
Output: 6
Explanation: The 6 subarrays are 
[0], [0], [0], [0], [0,0], and [0,0].

```


## Solution

```python

class Solution:
    #Function to count subarrays with sum equal to 0.
    def findSubArrays(self,arr,n):
        count = 0
        for i in range(n):
            if arr[i] == 0:
                count+=1
        ans = count        
        for i in range(n):
            for j in range(i+1,n):
                arr[i]+=arr[j]
                if  arr[i]== 0:
                    ans+=1
        return ans
```
#### Complexity
```bash
Time Complexity : O(n^2)
Space Complexity : O(1)

```

``` python
class Solution:
    def findSubArrays(self,arr,n):
        freq = {0:1}
        count = 0
        summ = 0
        
        for i in arr:
            summ+=i
            
            if summ in freq:
                count+=freq[summ]
                freq[summ]+=1
            else:
                freq[summ] = 1
        return count
```
```bash
Time Complexity : O(n)
Space Complexity : O(n)
```


## Geeksforgeeks
[Zero Sum Subarrays](https://practice.geeksforgeeks.org/problems/zero-sum-subarrays1825/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&company[]=Microsoft&company[]=Adobe&company[]=Facebook&category[]=Arrays&sortBy=submissions)
