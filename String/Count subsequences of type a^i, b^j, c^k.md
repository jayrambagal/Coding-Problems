## Count subsequences of type a^i, b^j, c^k
Given a string S, the task is to count number of subsequences of the form aibjck, where i >= 1, j >=1 and k >= 1.

Note: 
1. Two subsequences are considered different if the set of array indexes picked for the 2 subsequences are different.

3.  For large test cases, the output value will be too large, return the answer MODULO 10^9+7

## Example 
```bash
Input:
S = "abbc"
Output: 3
Explanation: Subsequences are abc, abc and abbc.

Input:
S = "abcabc"
Output: 7
Explanation: Subsequences are abc, abc,
abbc, aabc abcc, abc and abc.
```


## Solution 

```python
class Solution:
    def fun(self,s):
        a = 0
        b = 0
        c = 0
        for i in range(len(s)):
            if s[i]=="a":
                a = 1+2*a
            elif s[i]=="b":
                b = a+2*b
            else:
                c = b+2*c
        return c%1000000007

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

## Geeksforgeeks
[Count subsequences of type a^i, b^j, c^k](https://practice.geeksforgeeks.org/problems/count-subsequences-of-type-ai-bj-ck4425/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&category[]=Strings&sortBy=submissions)
