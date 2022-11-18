## Count Occurences of Anagrams
Given a word pat and a text txt. Return the count of the occurences of anagrams of the word in the text.

## Example 
```bash
Input:
txt = aabaabaa
pat = aaba
Output: 4
Explanation: aaba is present 4 times
in txt.

Input:
txt = forxxorfxdofr
pat = for
Output: 3
Explanation: for, orf and ofr appears
in the txt, hence answer is 3.
```


## Solution 

```python

class Solution:
    def search(self,pat, txt):
        res = 0
        for i in range(len(txt)-len(pat)+1):
            
            if (self.areAnagram(txt[i:i+len(pat)], pat)):
                res += 1
        return res
        
    def areAnagram(self,s1, s2):
        m = {}
        for i in range(len(s1)):
            if s1[i] not in m:
                m[s1[i]] = 1
            else:
                m[s1[i]] += 1
                
     
        for j in range(len(s2)):
            if s2[j] in m:
                m[s2[j]] -= 1
            else:
                return False
                
             
        for it in m.values():
           if(it != 0):
              return False
        return True
 ```
#### Complexity
```bash
Time Complexity :O()
Space Complexity : O()
```

## Solution 

```python

class Solution:
    def search(self,pat, string):
        n = len(string)
        k = len(pat)
        temp = []
        d = {}
        for i in pat:
            if i in d:
                d[i] += 1
            else:
                d[i] = 1
        i = 0
        j = 0
        count = len(d)
         
        ans = 0
         
         
        while j < n:
            if string[j] in d:
                d[string[j]] -= 1
                if d[string[j]] == 0:
                    count -= 1
            if (j-i+1) < k:
                j += 1
            elif (j-i+1) == k:
                if count == 0:
                    ans += 1
         
                if string[i] in d:
                    d[string[i]] += 1
                    if d[string[i]] == 1:
                        count += 1
         
                i += 1
                j += 1
        return ans
 ```
#### Complexity
```bash
Time Complexity :O()
Space Complexity : O()
```

## Geeksforgeeks
[Count Occurences of Anagrams](https://practice.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=sliding-window&sortBy=submissions)
