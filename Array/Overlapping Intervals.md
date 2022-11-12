## Overlapping Intervals
Given a collection of Intervals, the task is to merge all of the overlapping Intervals.

## Example 
```bash
Input:
Intervals = {{1,3},{2,4},{6,8},{9,10}}
Output: {{1, 4}, {6, 8}, {9, 10}}
Explanation: Given intervals: [1,3],[2,4]
[6,8],[9,10], we have only two overlapping
intervals here,[1,3] and [2,4]. Therefore
we will merge these two and return [1,4],
[6,8], [9,10].

```

## Solution 

```python
class Solution:
	def overlappedInterval(self, Intervals):
	    
	   		Intervals.sort()
	   		stack = []
	   		stack.append(Intervals[0])
	   		
	   		for i in Intervals[1:]:
	   		    
	   		    if stack[-1][0] <= i[0] <= stack[-1][-1]:
	   		        
	   		        stack [-1][-1] = max(stack[-1][-1], i[-1])
	   		       
	   		    else:
	   		        stack.append(i)
	   		        
	   		return stack
 ```
#### Complexity
```bash
Time Complexity :O(nlogn) + O(n)
Space Complexity : O(n)
```
## Geeksforgeeks
[Overlapping Intervals](https://practice.geeksforgeeks.org/problems/8a644e94faaa94968d8665ba9e0a80d1ae3e0a2d/1)
