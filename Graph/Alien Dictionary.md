## Alien Dictionary
Given a sorted dictionary of an alien language having N words and k starting alphabets of standard dictionary. Find the order of characters in the alien language.
Note: Many orders may be possible for a particular test case, thus you may return any valid order and output will be 1 if the order of string returned by the function 
is correct else 0 denoting incorrect string returned.

## Example 

```bash
Input: 
N = 5, K = 4
dict = {"baa","abcd","abca","cab","cad"}
Output:
1
Explanation:
Here order of characters is 
'b', 'd', 'a', 'c' Note that words are sorted 
and in the given language "baa" comes before 
"abcd", therefore 'b' is before 'a' in output.
Similarly we can find other orders.


Input: 
N = 3, K = 3
dict = {"caa","aaa","aab"}
Output:
1
Explanation:
Here order of characters is
'c', 'a', 'b' Note that words are sorted
and in the given language "caa" comes before
"aaa", therefore 'c' is before 'a' in output.
Similarly we can find other orders.

```

## Solution (DFS)

```python
from collections import deque
class Solution:
    def findOrder(self,dict, N, K):

        ## 1stly make adjoint list
        d=list(dict)
        adj=[]
        for i in range(K):
            adj.append([])

        for i in range(1,N):
            a=d[i-1]
            b=d[i]
            for j in range(min(len(a),len(b))):
                if(a[j]!=b[j]):
                    adj[(ord(a[j])-ord("a"))].append(ord(b[j])-ord("a"))
                    break
                
        ### making indegree of adj list and append to q which have ind[i]==0
        ind=[0]*K
        for i in adj:
            for j in i:
                ind[j]+=1

        q=deque([])

        for i in range(len(ind)):
            if(ind[i]==0):
                q.append(i)
        
        ans=[]

        #### simple topological sort
        
        while(len(q)!=0):
            cur=q.popleft()
            ans.append(cur)
            
            for k in adj[cur]:
                ind[k]-=1
                if(ind[k]==0):
                    q.append(k)
        
        rans=[]
        for i in range(len(ans)):
            ch=chr((ord('a')+ans[i]))
            rans.append(ch)
        return rans
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```

## Geeksforgeeks
[Alien Dictionary](https://practice.geeksforgeeks.org/problems/alien-dictionary/1)
