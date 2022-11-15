## Print Anagrams Together
Given an array of strings, return all groups of strings that are anagrams. The groups must be created in 

order of their appearance in the original array. Look at the sample case for clarification.

Note: The final output will be in lexicographic order.

## Example 
```bash
Input:
N = 5
words[] = {act,god,cat,dog,tac}
Output:
act cat tac 
god dog
Explanation:
There are 2 groups of
anagrams "god", "dog" make group 1.
"act", "cat", "tac" make group 2.

```

## Solution
```python
from collections import Counter

class Solution:

    def Anagrams(self, words, n):

        d = dict()

        for i in words:

            temp = str(sorted(dict(Counter(i))))

            if temp not in d:

                d[temp] = [i]

            else:

                d[temp].append(i)

        ans = []

        for k in sorted(d):

            ans.append(d[k])

        return ans
 ```
#### Complexity
```bash
Time Complexity :O()
Space Complexity : O()
```

## Geeksforgeeks
[Print Anagrams Together](https://practice.geeksforgeeks.org/problems/print-anagrams-together/1?page=1&status[]=unsolved&company[]=Amazon&category[]=Strings&sortBy=submissions)
