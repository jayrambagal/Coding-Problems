## Smallest distinct window

Given a string 's'. The task is to find the smallest window length that contains all the characters of the given string at least one time.
For eg. A = aabcbcdbca, then the result would be 4 as of the smallest window will be dbca.
## Example 
```bash
Input : "AABBBCBBAC"
Output : 3
Explanation : Sub-string -> "BAC"
```


## Solution 

```python
from collections import defaultdict
class Solution:
    def findSubString(self, strr):
        
        n = len(strr)
        
        if n <= 1:
            return len(strr)
            
        dist_count = len(set([x for x in strr]))
     
        curr_count = defaultdict(lambda: 0)
        count = 0
        start = 0
        min_len = n
     
        for j in range(n):
            curr_count[strr[j]] += 1
     
            if curr_count[strr[j]] == 1:
                count += 1
     
            if count == dist_count:
                while curr_count[strr[start]] > 1:
                    curr_count[strr[start]] -= 1
                    start += 1
     
                len_window = j - start + 1
     
                min_len = min(min_len,len_window)
        
        return min_len
        

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## CodeChef
[Smallest distinct window](https://practice.geeksforgeeks.org/problems/smallest-distant-window3132/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&category[]=Arrays&sortBy=submissions)
