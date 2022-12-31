## Find minimum number of Laptops required

There are N jobs and the start and finish time of the jobs are given in arrays start[] and end[] respectively. 

Each job requires one laptop and laptops can't be shared. Find the minimum number of laptops required given that 

you can give your laptop to someone else when you are not doing your job.

## Example 
```bash
Input:
N = 3
start[] = {1, 2, 3}
end[] = {4, 4, 6}
Output:
3
Explanation:
We can clearly see that everyone's supposed to
be doing their job at time 3. So, 3 laptops
will be required at minimum.

```
## Solution (optimized)

```python
class Solution: 
    def minLaptops(self, N, start, end):
        start.sort()
        end.sort()
        
        i,j,ans = 0,0,0
        
        while (i<N and j<N):
            if start[i]<end[j]:
                ans+=1
                i+=1
            else:
                i+=1
                j+=1
        return ans 

```
#### Complexity
```bash
Time Complexity :O(n) + O(nlogn)
Space Complexity : O(1)

```

## LeetCode
[Find minimum number of Laptops required](https://practice.geeksforgeeks.org/problems/af49b143a4ead583e943ca6176fbd7ea55b121ae/1)
