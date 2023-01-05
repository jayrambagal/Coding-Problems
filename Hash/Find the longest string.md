## Find the longest string
Given an array of strings arr[]. You have to find the longest string which is lexicographically smallest and 

also all of its prefix strings are already present in the array.
## Example 
```bash
Input: ab a aa abd abc abda abdd abde abdab
Output: abdab
Explanation: We can see that each string is fulfilling
the condition. For each string, all of its prefix 
are present in the array.And "abdab" is the longest
string among them. So the ouput is "abdab".

```
 
## Solution
```python
class Solution():

    def longestString(self, arr, n):

        arr.sort()
        max=""
        dict={}
        dict[""]=1
        
        for i in range(n):
            if arr[i][:-1] in dict:
                dict[arr[i]]=1
                
                if len(max)<len(arr[i]):
                    max=arr[i]
        return max
```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Find the longest string](https://practice.geeksforgeeks.org/problems/8d157f11af5416087251513cfc38ffc4d23be308/1)
