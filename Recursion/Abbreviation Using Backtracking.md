## Abbreviation Using Backtracking
1. You are given a word.
2. You have to generate all abbrevations of that word.

Use recursion as suggested in question video

 
## Example 1


```bash
Sample Input
pep

Sample Output
pep
pe1
p1p
p2
1ep
1e1
2p
3
```
## Solution 
```Python
def fun(strr, ans, count, pos):
    if pos == len(strr):
        if count == 0:
            print(ans)
        else:
            print(ans + str(count))
        return
    
    if count > 0:
        fun(strr, ans + str(count) + strr[pos], 0, pos + 1)
    else:
        fun(strr, ans + strr[pos], 0, pos + 1)
        
    fun(strr, ans, count + 1, pos + 1)

strr = input()
print(fun(strr, "", 0, 0))
    
```
```bash
Time Complexity : O(n)
Space Complexity : O(n-1) + O(n-1)
```
## Pepcoding

[Abrivation](https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/recursion-and-backtracking/abbreviation-suing-backtracking-official/ojquestion)
