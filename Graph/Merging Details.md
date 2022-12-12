## Merging Details
Bob, a teacher of St. Joseph School given a task by his principal to merge the details of the students where each element details[i] is a list of strings, where the first element details[i][0] is a name of the student, and the rest of the elements are emails representing emails of the student.   Two details definitely belong to the same student if there is some common email to both detail.  After merging the details, return the details of the student in the following format: the first element of each detail is the name of the student, and the rest of the elements are emails in sorted order. The details themselves can be returned in any order.  Note: Two details have the same name, they may belong to different people as people could have the same name. A person can have any number of details initially, but all of their details definitely have the same name.
Note: In case 2 or more same email belongs to 2 or more different names merge with first name only. Print in the order in sorted way according to the name of the details.

## Example 

```bash
Input: 
n: 4
details = 
[["John","johnsmith@mail.com","john_newyork@mail.com"],
["John","johnsmith@mail.com","john00@mail.com"],
["Mary","mary@mail.com"],
["John","johnnybravo@mail.com"]]
Output: 
[["John","john00@mail.com","john_newyork@mail.com",
"johnsmith@mail.com"],["Mary","mary@mail.com"],
["John","johnnybravo@mail.com"]]
Explanation:
The first and second John's are the same person as 
they have the common email "johnsmith@mail.com".
The third John and Mary are different people as none
of their email addresses are used by other accounts.
We could return these lists in any order, for example
the answer [['Mary', 'mary@mail.com'], 
['John', 'johnnybravo@mail.com'], 
['John', 'john00@mail.com', 'john_newyork@mail.com', 
'johnsmith@mail.com']] 
would still be accepted.
```



## Solution (disjoint set)
```python
class Solution:
    def mergeDetails(self,details):
        
        n = len(details)
        freq_parent = {}
        ds = desjointset(n)
        
        for i in range(n):
            for j in range(1,len(details[i])):
                mail = details[i][j]
                if details[i][j] not in freq_parent:
                    freq_parent[mail] = i
                else:
                    ds.union(i,freq_parent[mail])
                    
        mearge = [[] for i in range(n)]
        
        for mail,node in freq_parent.items():
            
            node = ds.find(node)
            mearge[node].append(mail)
        
        ans = []        
        for i in range(n):
            if mearge[i]==[]:
                continue
            mearge[i].sort()
            temp = []
            temp.append(details[i][0])
            
            for j in range(len(mearge[i])):
                temp.append(mearge[i][j])
                
            ans.append(temp)
        return ans
            
        
                    
class desjointset:
    def __init__(self,n):
        
        self.parent = [i for i in range(n)]
        self.rank = [1 for i in range(n)]
        
    def find(self,a):
        
        if self.parent[a]==a:
            return a
            
        self.parent[a] = self.find(self.parent[a])
        return self.parent[a]
        
    def union(self,a,b):
        
        pa = self.find(a)
        pb = self.find(b)
        
        if pa==pb:
            return 
        if self.rank[pa] > self.rank[pb]:
            self.parent[pb] = pa
            self.rank[pa]+= self.rank[pb]
        else:
            self.parent[pa] = pb
            self.rank[pb]+= self.rank[pa]
```
#### Complexity
```bash
Time Complexity : O(V^2) + O(4*alpha)
Space Complexity : O(V)
```
## Geeksforgeeks
[Merging Details](https://practice.geeksforgeeks.org/problems/merging-details/1)
