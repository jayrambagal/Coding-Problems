## Combination Sum
Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates 

where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the 

frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

## Example 1


```bash
Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```


## Solution 2 (optimization)

```Python

class Solution:
    def combinationSum(self, arr: List[int], target: int) -> List[List[int]]:

        ans = []
        out = []
        self.solve(0,out,arr,target,ans)
        return ans

    def solve(self,i,out,arr,target,ans):

        if i>len(arr)-1 or target<0:
            return
        if target==0:
            ans.append(out[::])
            return
            
        out.append(arr[i])
        self.solve(i,out,arr,target-arr[i],ans)
        out.pop()
        self.solve(i+1,out,arr,target,ans)
```
### Complexity
 
```bash
Time Complexity : 
Space Complexity : 
```

## Geeksforgeeks
[Combination Sum](https://leetcode.com/problems/combination-sum/description/)
