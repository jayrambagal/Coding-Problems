## Longest consecutive subsequence
```
Given an array of positive integers. Find the length of the longest sub-sequence such that 
elements in the subsequence are consecutive integers, the consecutive numbers can be in any order.
```

## Example 
```bash
Input:
Input:
N = 7
a[] = {2,6,1,9,4,5,3}
Output:
6
Explanation:
The consecutive numbers here
are 1, 2, 3, 4, 5, 6. These 6 
numbers form the longest consecutive
subsquence.

```

## Solution 

```python
class Solution:
    
    def findLongestConseqSubseq(self,arr, N):
        
        if N==1:
            return 1
        maxx = 0
        arr.sort()
        
        for i in range(N-1):
            count = 1
            
            for j in range(i,N-1):
                if arr[j+1]==arr[j]+1 :
                    count+=1
                elif arr[j+1]==arr[j]:
                    continue
                else:
                    
                    break
                
            maxx = max(maxx,count)
            
        return maxx
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
``` 
## Solution
```python
class Solution:
    
    def findLongestConseqSubseq(self,arr, N):
        
        if N==1:
            return 1
        maxx = 0
        count = 1
        arr.sort()
        
        for i in range(N-1):
          
            
            if arr[i+1] == arr[i]+1:
                count+=1
                maxx = max(maxx,count)
            elif arr[i+1]==arr[i]:
                continue
            else:
                count = 1
            maxx = max(maxx,count)
                
        return maxx
 ```
#### Complexity
```bash
Time Complexity :O(n + nlogn)
Space Complexity : O(1)
```

## Geeksforgeeks
[Longest consecutive subsequence](https://practice.geeksforgeeks.org/problems/longest-consecutive-subsequence2449/1?page=1&difficulty[]=1&status[]=unsolved&curated[]=1&sortBy=submissions)
