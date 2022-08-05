## Unbounded Knapsack
You are given 'N' items with certain 'PROFIT' and WEIGHT and a knapsack with weight capacity "W". You need to fill the
knapsack with the items in sucha way that you get the maximum profit. You are allowed to take one item multiple times.

#### Example
```bash
Input:
N = 3
W = 15
values[] = {7,2,4}
weight[] = {5,10,20}
Output: 21
```
### Solution 

```python
import sys
def unboundedKnapsack(n, w, profit, weight):
    
    return solve(n-1,w,profit,weight)

def solve(n,w,profit,weight):
    
    if n==0:
        ans = int(w/weight[0])*profit[0]
        return ans
    exclude = 0 + solve(n-1,w,profit,weight)
    include = -sys.maxsize
    if weight[n]<=w:
        include =profit[n] + solve(n,w-weight[n],profit,weight)
    
    return max(include,exclude)
        
```
### Complexity
```bash
Time Complexity = O(2^n)
Space Complexity = O(n) --> Auxilary space recursion
```
### Solution 

```python

```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n)+O(n) 
```![IMG_20220805_145315 1](https://user-images.githubusercontent.com/94613732/183047915-2c01656c-9acd-4ea6-af3c-01ca7c5b3d8a.jpg)
![IMG_20220805_145315 1](https://user-images.githubusercontent.com/94613732/183048061-514448f4-3648-4006-ac34-a830a678c239.jpg)


[Unbounded Knapsack](https://www.codingninjas.com/codestudio/problems/unbounded-knapsack_1215029?source=youtube&campaign=striver_dp_videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_dp_videos&leftPanelTab=0)

