## Optimal Partition of String
Given a string s, partition the string into one or more substrings such that the characters 

in each substring are unique. That is, no letter appears in a single substring more than once.

Return the minimum number of substrings in such a partition.

Note that each character should belong to exactly one substring in a partition.

## Example 
```bash
Input: s = "ssssss"
Output: 6
Explanation:
The only valid partition is ("s","s","s","s","s","s").

Input: s = "abacaba"
Output: 4
Explanation:
Two possible partitions are ("a","ba","cab","a") and ("ab","a","ca","ba").
It can be shown that 4 is the minimum number of substrings needed.

```


## Solution 

```python
class Solution:
    def partitionString(self, string: str) -> int:
            index=0
            countSet = set()
            substringCount = 1
            while index < len(string):
                if string[index] not in countSet:
                    countSet.add(string[index])
                    index+=1
                else:
                    countSet = set()
                    countSet.add(string[index])
                    substringCount+=1
                    index+=1

            return substringCount

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

 

## Leetcode-Contest
[Optimal Partition of String](https://leetcode.com/contest/weekly-contest-310/)
