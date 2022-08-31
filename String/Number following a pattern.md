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
            l,c,ans=1,1,''
            for i in S:
                if i=="D":
                    c+=1
                else:
                    x = c
                    while l<=x:
                        if str(x) not in ans:
                            ans+=str(x)
                        x-=1
                    l = c
                    c+=1
                
            while c>=l:
                if str(c) not in ans:
                    ans+=str(c)
                c-=1
            return ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

 

## Geeksforgeeks
[Number following a pattern](https://practice.geeksforgeeks.org/problems/number-following-a-pattern3126/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Google&category[]=Strings&sortBy=submissions)
