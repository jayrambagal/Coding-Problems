## Flood fill Algorithm
An image is represented by a 2-D array of integers, each integer representing the pixel value of the image.

Given a coordinate (sr, sc) representing the starting pixel (row and column) of the flood fill, and a pixel value newColor, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting 

pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of 

the aforementioned pixels with the newColor.

## Example 

```bash
Input: image = {{1,1,1},{1,1,0},{1,0,1}},
sr = 1, sc = 1, newColor = 2.
Output: {{2,2,2},{2,2,0},{2,0,1}}
Explanation: From the center of the image 
(with position (sr, sc) = (1, 1)), all 
pixels connected by a path of the same color
as the starting pixel are colored with the new 
color.Note the bottom corner is not colored 2, 
because it is not 4-directionally connected to 
the starting pixel.

```

## Solution

```python
class Solution:
	def floodFill(self, image, sr, sc, newColor):
		
		ans = image
		initial = image[sr][sc]
		row = [-1,0,1,0]
		col = [0,1,0,-1]
		
		self.dfs(image, sr, sc, newColor , ans , row , col,initial)
		
		return ans
		
	def dfs(self,image, sr, sc, newColor , ans , row , col,initial):
	    ans[sr][sc] = newColor
	    n = len(image)
	    m = len(image[0])
	    
	    for i in range(4):
	        n_row = sr + row[i]
	        n_col = sc + col[i]
	        
	        if (n_row in range(n) and n_col in range(m) 
	        and image[n_row][n_col]==initial 
	        and ans[n_row][n_col]!=newColor):
	            self.dfs(image, n_row, n_col, newColor , ans , row , col,initial)
 ```
#### Complexity
```bash
Time Complexity :
Space Complexity : 
```
## Geeksforgeeks
[Flood fill Algorithm](https://practice.geeksforgeeks.org/problems/flood-fill-algorithm1856/1)
