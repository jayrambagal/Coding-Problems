## Minimum Score Triangulation of Polygon

You have a convex n-sided polygon where each vertex has an integer value. You are given an integer array values where values[i] 

is the value of the ith vertex (i.e., clockwise order). You will triangulate the polygon into n - 2 triangles. For each triangle, 

the value of that triangle is the product of the values of its vertices, and the total score of the triangulation is the sum of these 

values over all n - 2 triangles in the triangulation. Return the smallest possible total score that you can achieve with some triangulation of the polygon.

#### Example
![image](https://user-images.githubusercontent.com/94613732/212524557-a70decde-ae62-465d-9a80-c58f3ec040d7.png)

```bash
Input: values = [3,7,4,5]
Output: 144
Explanation: There are two triangulations, with possible scores: 3*7*5 + 4*5*7 = 245, or 3*4*5 + 3*4*7 = 144.
The minimum score is 144.

```
![image](https://user-images.githubusercontent.com/94613732/212524575-a6c5cea6-d41d-467e-bf85-bbeb955a01fe.png)

```bash
Input: values = [1,3,1,4,1,5]
Output: 13
Explanation: The minimum score triangulation has score 1*1*3 + 1*1*4 + 1*1*5 + 1*1*1 = 13.
```
### Solution 

```python
class Solution:
    def minScoreTriangulation(self, values: List[int]) -> int:
        n = len(values)
        dp = [[0 for i in range(n)]for j in range(n)]

        for g in range(n):
            i = 0
            j = g
            while j<n:
                if g == 0:
                    dp[i][j] = 0
                elif g==1:
                    dp[i][j]=0
                elif g==2:
                    dp[i][j] = values[j]*values[j-1]*values[j-2]
                else:
                    maxx = 1e9
                    for k in range(i+1,j):
                        val = values[i]*values[k]*values[j]

                        left = dp[i][k]
                        right = dp[k][j]

                        ans = val+left+right
                        maxx = min(maxx,ans)
                    dp[i][j] = maxx
                i+=1
                j+=1
        print(dp)
        return dp[0][-1]

        
```
### Complexity
```bash
Time Complexity = O()
Space Complexity = O()
```


[Minimum Score Triangulation of Polygon](https://leetcode.com/problems/minimum-score-triangulation-of-polygon/description/)
