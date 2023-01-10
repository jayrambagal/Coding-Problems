## Minimum Number of Removals to Make Mountain Array
```
You may recall that an array arr is a mountain array if and only if:

arr.length >= 3
There exists some index i (0-indexed) with 0 < i < arr.length - 1 such that:
arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
arr[i] > arr[i + 1] > ... > arr[arr.length - 1]
Given an integer array nums​​​, return the minimum number of elements to remove to make nums​​​ a mountain array.
```
#### Example
```bash
Input: nums = [2,1,1,5,6,2,3,1]
Output: 3
Explanation: One solution is to remove the elements at indices 0, 1, and 5, making the array nums = [1,5,6,3,1].
```
### Solution 
```python
class Solution:
    def minimumMountainRemovals(self, arr: List[int]) -> int:
        n = len(arr)
        if n<=3:
            return 0
        
        # Finding Longest Increasing Subsequences
        lis = [0]*n
        lis[0]=1
        for i in range(1,n):
            count = 1
            for j in range(0,i):
                if arr[i]>arr[j]:
                    count = max(count,1+lis[j])
            lis[i] = count
        
        # Finding Longest Decreasing Subsequences
        lds = [0]*n
        lds[n-1]=1

        for i in range(n-1,-1,-1):
            count = 1
            for j in range(n-1,i,-1):
                if arr[i]>arr[j]:
                    count = max(count,1+lds[j])
            lds[i] = count
        
        # Calculating the answer
        res = 0
        for i in range(n):
            if lis[i]>1 and lds[i]>1:
                res = max(res,(lis[i]+lds[i])-2)
        return n-res-1
        
```
### Complexity
```bash
Time Complexity = O(n*n)
Space Complexity = O(n)+O(n) 
```


[Minimum Number of Removals to Make Mountain Array](https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/description/)
