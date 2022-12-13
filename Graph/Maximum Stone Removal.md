## Maximum Stone Removal
There are n stones at some integer coordinate points on a 2D plane. Each coordinate point may have at most one stone.

You need to remove some stones. 

A stone can be removed if it shares either the same row or the same column as another stone that has not been removed.

Given an array stones of length n where stones[i] = [xi, yi] represents the location of the ith stone, return the maximum possible 
number of stones that you can remove.

 
## Example 

```bash
Input:
n=6
[[0 0] ,[ 0 1], [1 0] ,[1 2] ,[2 1] ,[2 2]]

Output:
5

Example:
One way to remove 5 stones are
1--[0,0]
2--[1,0]
3--[0,1]
4--[2,1]
5--[1,2]
```

## Solution

```python
class Solution:
    def maxRemove(self, adj, n):
        
        max_row = 0
        max_col = 0
        
        for i in adj:
            max_row = max(max_row,i[0])
            max_col = max(max_col,i[1])
         
        ds = disjoinset(max_row+max_col+2)
        s = {}
        for i in adj:
            
            row_node = i[0]
            col_node = i[1]+max_row+1
            
            ds.union(row_node,col_node)
            s[row_node] = 1
            s[col_node] = 1
            
        count = 0
        
        for i in s:
            if ds.parent[i]==i:
                count+=1
        return len(adj)-count
            
            
class disjoinset:
    def __init__(self,n):
        self.parent = [i for i in range(n)]
        self.rank = [1 for i in range(n)]
        
    def find(self,a):
        if self.parent[a] == a:
            return a
        self.parent[a] = self.find(self.parent[a])
        
        return self.parent[a]
    
    def union(self,a,b):
        
        pa = self.find(a)
        pb = self.find(b)
        
        if pa == pb:
            return 
        
        if self.rank[pa]>self.rank[pb]:
            self.parent[pb] = pa
            self.rank[pa]+=self.rank[pb]
        else:
            self.parent[pa] = pb
            self.rank[pb]+=self.rank[pa]
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Maximum Stone Removal](https://practice.geeksforgeeks.org/problems/maximum-stone-removal-1662179442/1)
