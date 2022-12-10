## Floyd Warshall
The problem is to find the shortest distances between every pair of vertices in a given edge-weighted directed graph. 
The graph is represented as an adjacency matrix of size n*n. Matrix[i][j] denotes the weight of the edge from i to j. 
If Matrix[i][j]=-1, it means there is no edge from i to j.

Do it in-place.
## Example 

```bash
Input: matrix = {{0,25},{-1,0}}

Output: {{0,25},{-1,0}}

Explanation: The shortest distance between
every pair is already given(if it exists).
```
## question
```
what if graph contain loop 
then simplly check if arr[i][i] < 0  i.e arr[0][0],arr[1][1]
then graph contain loop
```
## Solution

```python
class Solution:
	def shortest_distance(self, arr):
	    
	    n = len(matrix)
	    
	    for i in range(n):
	        for j in range(n):
	            if arr[i][j]==-1:
	                arr[i][j] = 1e9
	                
	                
	    for k in range(n):
	        for i in range(n):
	            for j in range(n):
	                
	                arr[i][j] = min(arr[i][j] , arr[i][k] + arr[k][j])
	                
	    for i in range(n):
	        for j in range(n):
	            if arr[i][j]==1e9:
	                arr[i][j] = -1
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Floyd Warshall](https://practice.geeksforgeeks.org/problems/implementing-floyd-warshall2042/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implementing-floyd-warshall)
