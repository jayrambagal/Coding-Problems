## Detect Cycle using DSU
Given an undirected graph with V nodes and E edges. The task is to check if there 
is any cycle in undirected graph.
Note: Solve the problem using disjoint set union(dsu).

## Example 

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/204295853-d2462645-29cf-4e16-9fe9-026416a6813e.png)
```
Output:
Output: 1
Explanation: There is a cycle between 0->2->4->0
```

```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/204296034-e2760f24-b772-46e9-823d-2c9c75060c76.png)
```
Output: 0
Explanation: The graph doesn't contain any cycle
```

## Solution

```python
class Solution:

    def find_parent(self,parent,i):
        if parent[i]==i:
            return i
        else:
            return self.find_parent(parent,parent[i])
            
    def union(self,parent,x,y):
        parent[x] = y
        
    # main function 
    
	def detectCycle(self, V, adj):
	    
	    if V<=2:
	        return 0
		    
		parent = [0]*(V)
		
		for i in range(V):
		    parent[i] = i
		    
	    for i in range(V):
	        for j in adj[i]:
	            
	            x = self.find_parent(parent,i)
	            y = self.find_parent(parent,j)
	            
	            if x==y:
	                return 1
	            self.union(parent,x,y)
	    return 0
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Detect Cycle using DSU](https://practice.geeksforgeeks.org/problems/detect-cycle-using-dsu/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
