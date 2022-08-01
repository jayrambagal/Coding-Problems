## Minimum Swaps To Make Sequences Increasing

You are given two integer arrays of the same length nums1 and nums2. In one operation, you are allowed to swap nums1[i] with nums2[i].

For example, if nums1 = [1,2,3,8], and nums2 = [5,6,7,4], you can swap the element at i = 3 to obtain nums1 = [1,2,3,4] and nums2 = [5,6,7,8].
Return the minimum number of needed operations to make nums1 and nums2 strictly increasing. The test cases are generated so that the given input always makes it possible.

An array arr is strictly increasing if and only if arr[0] < arr[1] < arr[2] < ... < arr[arr.length - 1].
#### Example

```bash

Input: nums1 = [1,3,5,4], nums2 = [1,2,3,7]
Output: 1
Explanation: 
Swap nums1[3] and nums2[3]. Then the sequences are:
nums1 = [1, 3, 5, 7] and nums2 = [1, 2, 3, 4]
which are both strictly increasing.


Input: nums1 = [0,3,5,8,9], nums2 = [2,1,4,6,9]
Output: 1



```
### Solution (recursive)

```python
class Solution:
    def minSwap(self, nums1: List[int], nums2: List[int]) -> int:
        nums1.insert(0,-1)
        nums2.insert(0,-1)
        swapped = 0
        
        return self.solve(nums1,nums2,1,swapped)
    
    def solve(self,nums1,nums2,index,swapped):
        
        prev1 = nums1[index-1]
        prev2 = nums2[index-1]
        ans = 99999999
        
        if index==len(nums1):
            return 0
        
        if swapped == 1:
            temp = prev1
            prev1 = prev2
            prev2 = temp
            
        if nums1[index]> prev1 and nums2[index]>prev2:
            ans = self.solve(nums1,nums2,index+1,0)
            
        if nums1[index] > prev2 and nums2[index] > prev1:
            ans = min(ans,1 + self.solve(nums1,nums2,index+1,1))
        
        return ans
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution (Memoiation)

```python
### Solution 

```python

class Solution:
    def minSwap(self, nums1: List[int], nums2: List[int]) -> int:
        nums1.insert(0,-1)
        nums2.insert(0,-1)
        n = len(nums1)
        dp = [[-1 for _ in range(2)]for __ in range(n+1)]
        swapped = 0
        
        return self.solve(nums1,nums2,1,swapped,dp)
    
    def solve(self,nums1,nums2,index,swapped,dp):
        
        prev1 = nums1[index-1]
        prev2 = nums2[index-1]
        ans = 99999999
        
        if index==len(nums1):
            return 0
        
        if dp[index][swapped] != -1:
            return dp[index][swapped]
        
        if swapped == 1:
            temp = prev1
            prev1 = prev2
            prev2 = temp
            
        if nums1[index]> prev1 and nums2[index]>prev2:
            ans = self.solve(nums1,nums2,index+1,0,dp)
            
        if nums1[index] > prev2 and nums2[index] > prev1:
            ans = min(ans,1 + self.solve(nums1,nums2,index+1,1,dp))
            
        dp[index][swapped] = ans
        
        return dp[index][swapped]
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n)+O(n)
```
### Solution (Tabulation)
```python
class Solution:
    def minSwap(self, nums1: List[int], nums2: List[int]) -> int:
        nums1.insert(0,-1)
        nums2.insert(0,-1)
        n = len(nums1)
        dp = [[0 for _ in range(2)]for __ in range(n+1)]
        
        for index in range(n-1,0,-1):
            for swap in range(1,-1,-1):
                
                prev1 = nums1[index-1]
                prev2 = nums2[index-1]
                ans = 99999999
                
                if swap == 1:
                    temp = prev1
                    prev1 = prev2
                    prev2 = temp
            
                if nums1[index]> prev1 and nums2[index]>prev2:
                    ans = dp[index+1][0]
            
                if nums1[index] > prev2 and nums2[index] > prev1:
                    ans = min(ans,1 + dp[index+1][1])
            
                dp[index][swap] = ans
        
        return dp[index][1]                
```                
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n)
```       
[ Minimum Swaps To Make Sequences Increasing](https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/)

