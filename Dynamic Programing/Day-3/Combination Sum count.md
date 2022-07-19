## Combination Sum IV

the elements from the array are there such that the sum of chosen elements is equal to the target number tar.
Note: Two ways are considered the same if for every index the contents of both the ways are equal example way1=[1,2,3,1] and way2= [1,2,3,1] both way1 and way 2 are the same.
But if way1 =[1,2,3,4] and way2= [4,3,2,1] then both ways are different.
## Example 1


```bash
Input:
3 5
1 2 5
Output: 9

If N = 3 and tar = 5 and array elements are [1,2,5] then the number of possible ways of making sum = 5 are:
(1,1,1,1,1)
(1,1,1,2)
(1,2,1,1)
(2,1,1,1)
(1,1,2,1)
(2,2,1)
(1,2,2)
(2,1,2)
(5)
Hence the output will be 9.

```

## Solution 1 (Recursion)

```Python

def findWays(num: List[int], tar: int) -> int:
    if tar==0:
        
        return 1
    if tar <0:
        return 0
    ans=0
    for i in range(len(num)):
        ans += findWays(num,(tar-num[i]))
        
    return ans
        
```
### Complexity
 
```bash
Time Complexity : O(2^n)
Space Complexity : O(n)
```
## Solution 2 (Dynamic Programing)-->memoization

```Python
from typing import List

def findWays(num: List[int], tar: int) -> int:
    
    dp = [-1]*(tar+1)
    return solve(num,tar,dp)

def solve(num,tar,dp):
    if tar==0:
        return 1
    if tar <0:
        return 0
    if dp[tar] != -1:
        return dp[tar]
    ans=0
    for i in range(len(num)):
        ans += solve(num,(tar-num[i]),dp)
    dp[tar] = ans   
    
    return dp[tar]
```
### Complexity
 

```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n)
```
## Solution 3 (Dynamic Programing) --> Tabulation
```python 
 from typing import List

def findWays(num: List[int], tar: int) -> int:

    n = len(num)
    dp = [0 for _ in range(tar + 1)]
    
    dp[0] = 1
    for i in range(1, tar+1):   # n time complexity
        for j in range(n):      # m 

            if i - num[j] >= 0:
                dp[i] += dp[i - num[j]]

    return dp[tar]
    
```
```bash
Time Complexity : O(n*m)
Space Complexity : O(n)
```
## Solution 3 (Dynamic Programing) --> Space Optimization
```Python
#Space optimization  Not Possible

```
```bash
Time Complexity : O(n)
Space Complexity : O(1)
```
## GeeksforGeeks
[Combination Sum IV](https://www.codingninjas.com/codestudio/problems/number-of-ways_3755252?leftPanelTab=1&utm_source=youtube&utm_medium=affiliate&utm_campaign=Lovebabbar)
