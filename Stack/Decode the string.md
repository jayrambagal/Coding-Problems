## Decode the string
An encoded string (s) is given, and the task is to decode it. The encoding pattern is that the occurrence 

of the string is given at the starting of the string and each string is enclosed by square brackets.

Note: The occurance of a single string is less than 1000.

#### Example
```bash
Input: s = 3[b2[ca]]
Output: bcacabcacabcaca
Explaination: 2[ca] means 'ca' is repeated 
twice which is 'caca' which concatenated with 
'b' becomes 'bcaca'. This string repeated 
thrice becomes the output.

```
### Solution 

```python
class Solution:
    def decodedString(self, s):
        
        stack = []
        num = 0
        cur_str = ""
        
        for i in s:
            
            if i.isdigit():
                num = num*10 + int(i)
            elif i.isalpha():
                cur_str+=i
            elif i == "[":
                stack.append((num,cur_str))
                num = 0
                cur_str = ""
                
            else:
                prev_num , prev_str = stack.pop()
                
                cur_str = prev_str + prev_num*cur_str
                
        return cur_str
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n) 
```

## Geeksforgeeks      
[Decode the string](https://practice.geeksforgeeks.org/problems/decode-the-string2444/1?page=1&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Stack&category[]=Queue&category[]=two-pointer-algorithm&category[]=sliding-window&sortBy=submissions)
