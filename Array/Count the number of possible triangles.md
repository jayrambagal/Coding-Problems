## Count the number of possible triangles
Given an unsorted array arr[] of n positive integers. Find the number of triangles 

that can be formed with three different array elements as lengths of three sides of triangles. 

## Example 
```bash
Input: 
n = 3
arr[] = {3, 5, 4}
Output: 
1
Explanation: 
A triangle is possible 
with all the elements 5, 3 and 4.

```

## Solution 

```python

 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(1)
```


## Solution 

```python
class Solution:
    #Function to count the number of possible triangles.
    def findNumberOfTriangles(self, arr, n):
        count = 0
        for i in range(n-2):
            for j in range(i+1,n-1):
                for k in range(j+1,n):
                    if arr[i] + arr[j] > arr[k] and arr[i] < arr[j] + arr[k] and arr[i] + arr[k] > arr[j]:
                        count+=1
                    
        return count
 ```
#### Complexity
```bash
Time Complexity :O(n^3)
Space Complexity : O(1)
```


## Solution
```python
class Solution:
    #Function to count the number of possible triangles.
    def findNumberOfTriangles(self, arr, n):
        
        arr.sort()
        count = 0
        
        for i in range(n-1,1,-1):
            l = 0
            r = i-1
            
            while l<r:
                
                if arr[l]+arr[r] > arr[i]:
                    count += (r-l)
                    r-=1
                    
                else:
                    l+=1
                    
        return count
 ```
 

## Geeksforgeeks
[Count the number of possible triangles](https://practice.geeksforgeeks.org/problems/count-possible-triangles-1587115620/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&sortBy=submissions)
