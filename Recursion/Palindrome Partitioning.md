## Palindrome Partitioning
Given a string s, partition s such that every 
substring
 of the partition is a 
palindrome
. Return all possible palindrome partitioning of s.

## Example 1


```bash
Input: s = "aab"
Output: [["a","a","b"],["aa","b"]]

Input: s = "a"
Output: [["a"]]
```
![image](https://user-images.githubusercontent.com/94613732/210333090-23f03b31-ccc8-4e3c-9b5a-f737d64a3173.png)


## Solution

```Python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res = []
        curr_part = []

        def backtrack(i):
            if i >= len(s):
                res.append(curr_part[:])
                return

            for j in range(i, len(s)):
                if isPalindrome(s[i: j + 1]):
                    curr_part.append(s[i: j + 1])
                    backtrack(j + 1)
                    curr_part.pop()

        backtrack(0)
        return res


def isPalindrome(s):
    if s==s[::-1]:
        return True
    else:
        return False
```
### Complexity
 
```bash
Time Complexity : O( (2^n) *k*(n/2) )
Space Complexity : O(k * x)
```

## Geeksforgeeks
[Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/description/)
