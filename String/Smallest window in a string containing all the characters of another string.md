## Smallest window in a string containing all the characters of another string

Given two strings S and P. Find the smallest window in the string S consisting of all the 

characters(including duplicates) of the string P.  Return "-1" in case there is no such window present. 

In case there are multiple such windows of same length, return the one with the least starting index. 

## Example 
```bash
Input:
S = "timetopractice"
P = "toc"
Output: 
toprac
Explanation: "toprac" is the smallest
substring in which "toc" can be found.
```


## Solution 

```python
class Solution:

    def smallestWindow(self, s, p):
       
        n = len(s)
        if n < len(p):
            return -1
        mp = [0]*256
     
        start = 0
        ans = n + 1
        cnt = 0

        for i in p:
            mp[ord(i)] += 1
            if mp[ord(i)] == 1:
                cnt += 1

        j = 0
        i = 0

        while(j < n):

            mp[ord(s[j])] -= 1
            if mp[ord(s[j])] == 0:
                cnt -= 1

                while cnt == 0:
                    if ans > j - i + 1:

                        ans = j - i + 1
                        start = i

                    mp[ord(s[i])] += 1
                    if mp[ord(s[i])] > 0:
                        cnt += 1
                    i += 1
            j += 1
        if ans > n:
            return "-1"
        return s[start:start+ans]
        

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```

## CodeChef
[Smallest window in a string containing all the characters of another string](https://practice.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&company[]=Amazon&category[]=Strings&sortBy=submissions)
