## Number following a pattern
Given a pattern containing only I's and D's. I for increasing and D for decreasing.

Devise an algorithm to print the minimum number following that pattern.

Digits from 1-9 and digits can't repeat. 

## Example 
```bash
Input:
D
Output:
21
Explanation:
D is meant for decreasing,
So we choose the minimum number
among 21,31,54,87,etc.

```

## Solution 

```python
class Solution:
    def printMinNumberForPattern(ob,S):
        
        ans = ""
        count = 1
        start = 1
        
        for i in S:
            if i=="D":
                count+=1
            else:
                ind = count
                
                while start<= ind:
                    if str(ind) not in ans:
                        ans+=str(ind)
                    ind-=1
                    
                start = count
                count+=1
                
        while start<= count:
            if str(count) not in ans:
                ans+=str(count)
            count-=1
        
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

 

## Geeksforgeeks
[Number following a pattern](https://practice.geeksforgeeks.org/problems/number-following-a-pattern3126/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Google&category[]=Strings&sortBy=submissions)
