## Maximum Expression
You are given a string SS of length NN, consisting of the digits 0-9 and the characters '+' and '-'. SS represents a valid mathematical expression.

Rearrange the characters of SS to form a valid mathematical expression such that the result obtained upon evaluating it is maximum.

If there are multiple possible answers, you may print any of them.

Note: A string SS of length NN is said to be a valid mathematical expression if the following hold:

The first character of SS is not + or -.
The last character of SS is not + or -.
Any + or - in SS must not be adjacent to another + or -.
In particular, numbers are allowed to have leading zeros, and adding/subtracting zero is fine.

## Example 
```bash
Input:

3
7
4-89+20
5
5-9+0
3
9-5

Output:

984+2-0
5+9-0
9-5
```


## Solution 

```python
def solve(s,n):
    demo = []
    add = 0
    sub = 0
    for i in range(n):
        try:
            a = int(s[i])
            demo.append(a)
        except:
            if s[i]=="+":
                add+=1
            else:
                sub +=1
        
    demo.sort()
    demo_len = len(demo)
    ran = (add+sub)-1
    j=0
    ans = ""
    for i in range(demo_len-1,ran,-1):
        ans+=str(demo[i])
        j=i
    j = j-1
    while j>=0:
        if add>0:
            add-=1
            ans+="+"
        elif sub>0:
            sub-=1
            ans+="-"
        ans+=str(demo[j])
        j-=1
        
    return ans
            
            
for _ in range(int(input())):
    n = int(input())
    s = input()
    print(solve(s,n))

 ```
#### Complexity
```bash
Time Complexity :O(n) + O(n) + O(n log n)
Space Complexity : O(n)
```

## CodeChef
[Maximum Expression](https://www.codechef.com/submit/MAXEXP)
