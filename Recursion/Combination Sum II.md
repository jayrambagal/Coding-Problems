## Combination Sum II
Given a collection of candidate numbers (candidates) and a target number (target), find all unique 

combinations in candidates where the candidate numbers sum to target.

Each number in candidates may only be used once in the combination.

Note: The solution set must not contain duplicate combinations.

## Example 1


```bash
Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
].
```


## Solution  

```Python
class Solution:
    def combinationSum2(self, arr: List[int], target: int) -> List[List[int]]:
        if not arr:
            return []
        arr.sort()
        ans = []
        self.solve(arr, target, 0, [], ans)
        return ans

    def solve(self, arr, target, ind, path, ans):
        if target == 0:
            ans.append(path)
        
        for i in range(ind, len(arr)):
            if arr[i] > target:
                break
            if i > ind and arr[i] == arr[i-1]:
                continue
            self.solve(arr, target-arr[i], i+1, path+[arr[i]], ans)
```
### Complexity
 
```bash
Time Complexity : O(nlogn) +  O(2^n) * k   k is the len(out)
Space Complexity : 
```

## Geeksforgeeks
[Combination Sum II](https://leetcode.com/problems/combination-sum-ii/description/)
