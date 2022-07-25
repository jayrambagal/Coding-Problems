## House Robber II
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

 
## Example 1


```bash
Input: nums = [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.


Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```
## Solution 3 (Dynamic Programing) --> Tabulation and space optimization
```Python
class Solution:
    
    def solve(self,arr,n):
        prev1 = arr[0]
        prev2 = 0
        
        for i in range(1,n-1):
            include = prev2 + arr[i]
            exclude = prev1 + 0
            ans = max(include,exclude)
            prev2 = prev1
            prev1 = ans
        return prev1
    
    def rob(self, valueInHouse: List[int]) -> int:
        n=len(valueInHouse)
        if n==1:
            return valueInHouse[0]
        solution1 = []*n
        solution2 = []*n
    
        for i in range(n):
            
            
            if i!=n-1:
                
                solution1.append(valueInHouse[i])
            
            if i!=0:
                solution2.append(valueInHouse[i])
            
        return max(self.solve(solution1,n),self.solve(solution2,n))
    
```
```bash
Time Complexity : O(n)
Space Complexity : O(n-1) + O(n-1)
```
## LeetCode
[House Robber II](https://leetcode.com/problems/house-robber-ii/)
