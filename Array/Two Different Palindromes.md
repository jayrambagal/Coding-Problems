## Two Different Palindromes
You are given two positive integers AA and BB. You need to construct two different binary strings

(i.e, they are strings which consist of only 00s and 11s), which satisfy these two conditions:

Both the strings should be palindromes.
Each string should have exactly AA 00s, and exactly BB 11s in them.
Output Yes if two such different binary strings can be constructed and No otherwise.

Note:

A string is said to be a palindrome, if the string and the reverse of the string are identical.
Two strings are said to be different if either their lengths are different, or if they differ in at least one character.

## Example 
```bash
Input

3
2 2
2 3
3 3

Output
Yes
Yes
No

```

## Solution 

```python
def palindrome(s):
    i = 0
    j = len(s)-1
    while i<j:
        if s[i]!=s[j]:
            return False
        i+=1
        j-=1
    return True

def solve(a,b):
    
    ans = ""
    for i in range(b):
        ans+="1"
    for i in range(a):
        ans+="0"
        
    count = 0
    lenth = (a+b ) 
    i = 0
    
    while count<lenth:
        if palindrome(ans[i:]) == True:
            return "Yes"
        else:
            temp = ans[i]
            ans+=temp
            count+=1
            i+=1
    return "No"
            
        
    
t = int(input())

for i in range(t):
    
    a,b = map(int,input().split())
    
    print(solve(a,b))
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```


## Solution 

```python
def solve(a,b):
    
    if a == 1 or b == 1:
        return "No"
        
    if a%2!=0 and b%2!=0:
        return "No"
        
    return "Yes"
    
t = int(input())

for i in range(t):
    
    a,b = map(int,input().split())
    
    print(solve(a,b))

    
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```


 

## CodeChef
[Two Different Palindromes](https://www.codechef.com/submit/TWODIFFPALIN?tab=statement)
