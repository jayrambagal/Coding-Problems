## Maximum Score Words Formed by Letters
Given a list of words, list of  single letters (might be repeating) and score of every character.

Return the maximum score of any valid set of words formed by using the given letters (words[i] cannot be used two or more times).

It is not necessary to use all characters in letters and each letter can only be used once. Score of letters 'a', 'b', 'c', ... ,'z' 


is given by score[0], score[1], ... , score[25] respectively.

 
## Example 1

```bash

Input: words = ["dog","cat","dad","good"], 
letters = ["a","a","c","d","d","d","g","o","o"], 
score = [1,0,9,5,0,0,3,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,0,0,0,0]

Output: 23

Explanation:
Score  a=1, c=9, d=5, g=3, o=2
Given letters, we can form the words "dad" (5+1+5) and "good" (3+2+2+5) with a score of 23.
Words "dad" and "dog" only get a score of 21.
```

![IMG_20230104_183659 1](https://user-images.githubusercontent.com/94613732/210562497-5a004937-f176-4d6e-9b07-89792fbbc1d7.jpg)

## Solution 
```Python

class Solution:
    def maxScoreWords(self, words: List[str], letters: List[str], score: List[int]) -> int:
        
        freq  = collections.Counter(letters)
        return self.solve(words,freq,score,0)

    def solve(self,words,freq,score,ind):

        if ind == len(words):
            return 0
        NotTake = self.solve(words,freq,score,ind+1)

        Str = words[ind]
        Flag = True
        StrScore = 0

        for ch in Str:
            if freq[ch]==0:
                Flag = False
            freq[ch]-=1
            StrScore+=score[ord(ch)-ord('a')]

        Take = 0
        if Flag:
            Take = StrScore + self.solve(words,freq,score,ind+1)
        
        for ch in Str:
            freq[ch]+=1
        return max(NotTake,Take)
    
```
```bash
Time Complexity : O()
Space Complexity : O() 
```
## LeetCode

[Maximum Score Words Formed by Letters](https://leetcode.com/problems/maximum-score-words-formed-by-letters/description/)
