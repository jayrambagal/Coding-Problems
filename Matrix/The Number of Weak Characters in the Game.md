## The Number of Weak Characters in the Game
```
You are playing a game that contains multiple characters, and each of the characters has two main properties: 
attack and defense. You are given a 2D integer array properties where properties[i] = [attacki, defensei] 
represents the properties of the ith character in the game. A character is said to be weak if any other 
character has both attack and defense levels strictly greater than this character's attack and defense levels. 
More formally, a character i is said to be weak if there exists another character j where attackj > attacki and 
defensej > defensei. Return the number of weak characters.
```

## Example 
```bash
Input: properties = [[1,5],[10,4],[4,3]]
Output: 1
Explanation: The third character is weak because the second character has a strictly greater attack and defense.


```
## Solution

```python
class Solution:
    def numberOfWeakCharacters(self, properties: List[List[int]]) -> int:
        
        n = len(properties)
        properties.sort(key = lambda x: (-x[0], x[1]))
        
        count = 0
        mx = 0
        
        for arr in properties:
            if arr[1] < mx:
                count+=1
                
            mx = max(mx,arr[1])
            
        return count
```
## Complexity

```
Time Complexity : O(nlogn)+O(n)
Space Complexity : O(1)
```
## Leetcode
[The Number of Weak Characters in the Game](https://leetcode.com/problems/the-number-of-weak-characters-in-the-game/)


