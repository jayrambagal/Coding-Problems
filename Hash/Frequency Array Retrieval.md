## Frequency Array Retrieval
```
Consider an array AA consisting of NN positive elements. The frequency array of AA is 
the array BB of size NN such that Bi = frequency of element Ai in AA.

For example, if A = [4, 7, 4, 11, 2, 7, 7]A=[4,7,4,11,2,7,7], the frequency array B = [2, 3, 2, 1, 1, 3, 3]B=[2,3,2,1,1,3,3].

You have lost the array AA, but fortunately you have the array BB.
Your task is to construct the lexicographically smallest array AA such that:


```


## Example 
```bash
INPUT :
5
5
2 3 3 3 2
5
1 1 1 1 1
5
5 5 5 5 5
3
1 2 4
8
1 3 2 3 2 2 2 3

OUTPUT :
1 2 2 2 1
1 2 3 4 5
1 1 1 1 1
-1
1 2 3 2 3 4 4 2


```

## Solution 
```python
import collections
for _ in range(int(input())):
	n = int(input())
	b = list(map(int, input().split()))
  
	freq = collections.Counter(b)
	curval = {}
	nxt = 1
	a = [-1]*n
  
	for i in range(n):
		if freq[b[i]]%b[i] == 0:
			curval[b[i]] = nxt
			nxt += 1
		if b[i] not in curval: break
		freq[b[i]] -= 1
		a[i] = curval[b[i]]
    
	if min(a) == -1: print(-1)
	else: print(*a)
        
```
#### Complexity
```bash
Time Complexity : O(n)
Space Complexity : O(n)+O(n) 
```

## Geeksforgeeks
[Frequency Array Retrieval](https://www.codechef.com/START70D?order=desc&sortBy=successful_submissions)
