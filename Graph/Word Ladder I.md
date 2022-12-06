## Word Ladder I
Given two distinct words startWord and targetWord, and a list denoting wordList of unique words of equal lengths. Find the length of the shortest transformation sequence from startWord to targetWord.
Keep the following conditions in mind:

A word can only consist of lowercase characters.
Only one letter can be changed in each transformation.
Each transformed word must exist in the wordList including the targetWord.
startWord may or may not be part of the wordList
The second part of this problem can be found here.

Note: If no possible way to transform sequence from startWord to targetWord return 0

## Example 

```bash
Input:
wordList = {"des","der","dfr","dgt","dfs"}
startWord = "der", targetWord= "dfs",
Output:
3
Explanation:
The length of the smallest transformation
sequence from "der" to "dfs" is 3
i,e "der" -> "dfr" -> "dfs".


Input:
wordList = {"geek", "gefk"}
startWord = "gedk", targetWord= "geek", 
Output:
2
Explanation:
gedk -> geek

```

## Solution (DFS)

```python
from string import ascii_lowercase
from collections import deque

class Solution:
	def wordLadderLength(self, startWord, targetWord, wordList):
		
		hash_map = {}
		for i in range(len(wordList)):
		    hash_map[wordList[i]] = 1
		    
		q = deque([])
		q.append((startWord,0))
		
		while q:
		    word , step = q.popleft()
		    if word == targetWord:
		        return step+1
		        
		    for i in range(len(word)):
		        w = word
		        for j in ascii_lowercase:
		            w = w[:i] + j + w[i+1:]
		            if w in hash_map:
		                q.append((w,step+1))
		                del hash_map[w]
        return 0 
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```

## Geeksforgeeks
[Word Ladder I](https://practice.geeksforgeeks.org/problems/word-ladder/1)
