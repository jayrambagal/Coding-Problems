## Longest K unique characters substring

Given a string you need to print the size of the longest possible substring that has exactly K unique characters. 

If there is no possible substring then print -1.

## Example 
```bash
Input:
S = "aabacbebebe", K = 3
Output: 7
Explanation: "cbebebe" is the longest 
substring with K distinct characters.
```


## Solution 

```python

class Solution:

    def longestKSubstr(self, s, k):
        dic={}
        i=0
        j=0
        res=-1

        while j<len(s):

            if s[j] not in dic:
                dic[s[j]]=1
            else:
                dic[s[j]]+=1

            if len(dic)<k:
                j+=1

            elif len(dic)==k:
                res=max(res,j-i+1)
                j+=1

            if len(dic)>k:
                while len(dic)>k:
                    if dic[s[i]]==1:
                        del dic[s[i]]
                        i+=1
                    else:
                        dic[s[i]]-=1
                        i+=1
                j+=1
                
        return res
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```


## Geeksforgeeks
[Longest K unique characters substring](https://practice.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Stack&category[]=Queue&category[]=two-pointer-algorithm&category[]=sliding-window&sortBy=submissions)
