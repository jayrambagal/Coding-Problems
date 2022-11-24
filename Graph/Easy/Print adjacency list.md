## Print adjacency list
Given the adjacency list of a bidirectional graph. Your task is to copy/clone the adjacency list for each vertex and return a new list.

## Example 
```bash
Input:
```
![image](https://user-images.githubusercontent.com/94613732/203698650-d0c45619-debe-4295-a06c-1149434a81ed.png)

```bash
Output: 
0-> 1-> 4 
1-> 0-> 2-> 3-> 4 
2-> 1-> 3 
3-> 1-> 2-> 4 
4-> 0-> 1-> 3
Explanation:
As 0,1 and 3 is connected to 4 so 4th row
of the list containing 4 and its connected
nodes 0,1 and 3 and we have to add those in
sorted order and same for every row.

```

## Solution 

```python
#User function Template for python3

class Solution:
    
    #Function to return the adjacency list for each vertex.
    def printGraph(self, V, adj):
        ans = []
        
        for node in adj:
            ans.append(node)
            
        for j in range(len(ans)):
            ans[j].insert(0,j)
            
        return ans
        


#{ 
 # Driver Code Starts
if __name__ == '__main__':

	T=int(input())
	for i in range(T):
		V, E = map(int, input().split())
		adj = [[] for i in range(V)]
		for _ in range(E):
			u, v = map(int, input().split())
			adj[u].append(v)
			adj[v].append(u)
		obj = Solution()
		ans = obj.printGraph(V, adj)
		for i in range(len(ans)):
		    for j in range(len(ans[i])-1):
		        print(ans[i][j], end = "-> ")
		    print(ans[i][len(ans[i])-1]);

# } Driver Code Ends
 ```
#### Complexity
```bash
Time Complexity :O(V) + O(V)
Space Complexity : O(V)
```
## Geeksforgeeks
[Print adjacency list](https://practice.geeksforgeeks.org/problems/print-adjacency-list-1587115620/1?page=1&difficulty[]=0&status[]=unsolved&category[]=Graph&sortBy=submissions)
