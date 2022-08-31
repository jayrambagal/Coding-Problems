## Repeated String Match
Given two strings A and B, find the minimum number of times A has to be repeated 

such that B becomes a substring of the repeated A. If B cannot be a substring of A 

no matter how many times it is repeated, return -1.

## Example 
```bash
Input: A = "abcd", B = "cdabcdab"
Output: 3
Explanation: After repeating A three times, 
we get "abcdabcdabcd".

```


## Solution 

```python
class Solution:
    def repeatedStringMatch(self, A, B):
        
        count = 1
        for i in range(len(B)):
            if B in A:
                return count
            else:
                A+=A
                count+=1
        return -1
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```


## Solution
```python
class Solution:
    def repeatedStringMatch(self, a, b):
        
        counter = 1
        tmp = a
        while (len(a)<len(b)):
            a+=tmp
            counter+=1
        if b in a:
            return counter
        if b in a+tmp:
            return counter+1
        return -1
 ```
 

## Geeksforgeeks
[Repeated String Match](https://practice.geeksforgeeks.org/problems/0cba668df04d657fde4d1bd28b626a01e61097f1/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Google&category[]=Strings&sortBy=submissions)
