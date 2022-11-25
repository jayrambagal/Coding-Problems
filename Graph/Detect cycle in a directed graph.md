## Detect cycle in a directed graph
Given a Directed Graph with V vertices (Numbered from 0 to V-1) and E edges, check whether it contains any cycle or not.

## Example 

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/203939886-2e7f7876-867b-434c-aa09-ff405647c0ec.png)


```bash
Output : 1

```

## Solution 

```python
class Solution:
    def isCyclic(self, V, adj):
        
        ver=[False]*(V)
        h=[False]*(V)

        def val(ver,h,adj,s):
            ver[s]=True
            h[s]=True

            for i in adj[s]:
                if h[i]==True:
                    return True
                    
                if ver[i]==False:
                    if val(ver,h,adj,i)==True:
                        return True

            h[s]=False

            return False

        for j in range(V):
            if val(ver,h,adj,j)==True:
                return True

        return False
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Solution 

```python


     

        
        

 ```
#### Complexity
```bash
Time Complexity :O(V) + O(E)
Space Complexity : O(V)
```
## Geeksforgeeks
[Detect cycle in a directed graph](https://practice.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1?page=1&difficulty[]=0&difficulty[]=1&category[]=Graph&sortBy=submissions)
