## Counting elements in two arrays
Given two unsorted arrays arr1[] and arr2[]. They may contain duplicates. 

For each element in arr1[] count elements less than or equal to it in array arr2[].

## Example 
```bash
Input:
m = 6, n = 6
arr1[] = {1,2,3,4,7,9}
arr2[] = {0,1,2,1,1,4}
Output: 4 5 5 6 6 6
Explanation: Number of elements less than
or equal to 1, 2, 3, 4, 7, and 9 in the
second array are respectively 4,5,5,6,6,6

```

## Solution 

```python
class Solution:
    def countEleLessThanOrEqual(self,arr1,n1,arr2,n2):
        arr2.sort()
        ans = []
        for i in range(n1):
            count = 0
            for j in range(n2):
                if arr1[i]>=arr2[j]:
                    count+=1
                else:
                    break
            ans.append(count)
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(n)

```
## Solution (binary search)
```python
class Solution:
    def countEleLessThanOrEqual(self,arr1,n1,arr2,n2):
       
        arr2.sort()
        ans =[]
       
        for i in range(n1):
           
            index = self.solve(arr2,n2,arr1[i])
            
            ans.append(index+1)
            
        return ans
           
    def solve(self,arr,n,target):
        l = 0
        h = n-1
        while l<=h:
            mid = int((l+h)//2)
            
            if arr2[mid] <= target:
                l = mid+1
            else:
                h = mid-1
                
        return h
```
#### Complexity
```bash
Time Complexity :O(n * logn) 
Space Complexity : O(n)

```

## Geeksforgeeks
[Counting elements in two arrays](https://practice.geeksforgeeks.org/problems/counting-elements-in-two-arrays/1)
