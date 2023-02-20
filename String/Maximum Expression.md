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
t = int(input())
for i in range(t):
    m = int(input())
    s = input()
    
    
    add = 0
    sub = 0
    arr = []
    
    for i in s:
        if i=="+":
            add+=1
        elif i == "-":
            sub+=1
        else:
            arr.append(i)
    arr.sort()
    
    n = len(arr)
    ans = ""
    j = n-1
    i = add+sub
    
    while j>=0:
        
        while j>=i:
            ans+=str(arr[j])
            j-=1
        
        if add>0:
            ans+= "+"
            add-=1
        elif sub>0:
            ans+= "-"
            sub-=1
            
        i = add+sub
        
    print(ans)

 ```
#### Complexity
```bash
Time Complexity :O(n) + O(n) + O(n log n)
Space Complexity : O(n)
```

## CodeChef
[Maximum Expression](https://www.codechef.com/submit/MAXEXP)
