## Sorting Elements of an Array by Frequency
```
Given an array of integers, sort the array according to frequency of elements. 
That is elements that have higher frequency come first. If frequencies of two 
elements are same, then smaller number comes first.
```

## Example 
```bash
Input:
N = 5
A[] = {5,5,4,6,4}
Output: 4 4 5 5 6
Explanation: The highest frequency here is
2. Both 5 and 4 have that frequency. Now
since the frequencies are same then 
smallerelement comes first. So 4 4 comes 
firstthen comes 5 5. Finally comes 6.
The output is 4 4 5 5 6.

```
## Solution
```python

from collections import defaultdict 
class Solution:
   
    def sortByFreq(self,arr,n):
        
        d = defaultdict(lambda: 0)
        for i in range(n):
            d[arr[i]] += 1
    
        arr.sort(key=lambda x: (-d[x], x))
     
        return arr
        

 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Sorting Elements of an Array by Frequency](https://practice.geeksforgeeks.org/problems/sorting-elements-of-an-array-by-frequency-1587115621/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&sortBy=submissions)
