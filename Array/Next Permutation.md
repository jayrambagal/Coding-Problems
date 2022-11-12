## Next Permutation
Implement the next permutation, which rearranges the list of numbers into Lexicographically next greater permutation 

of list of numbers. If such arrangement is not possible, it must be rearranged to the lowest possible order i.e. 

sorted in an ascending order. You are given an list of numbers arr[ ] of size N.

## Example 
```bash
Input: N = 6
arr = {1, 2, 3, 6, 5, 4}
Output: {1, 2, 4, 3, 5, 6}
Explaination: The next permutation of the 
given array is {1, 2, 4, 3, 5, 6}.

```

## Algorithm
```
step1 : traversing through back of the array and finding
              arr[ind] < arr[ind+1]  and store in index1.
step2 : again traversing through back and find 
              arr[ind] > arr[index1] and stroe in index2.
step3 : swap(arr[index1],arr[index2])

step4 : reverse the arr from index1+1 to end and return the answer.
```


## Solution 

```python
class Solution:
    def nextPermutation(self, N, arr):
        ind = 0
        l = []
        l += arr
        for i in range(N-2, -1, -1):
            if l[i]<l[i+1]:
                ind = i
                break
        for i in range(N-1, ind, -1):
            if l[i]>l[ind]:
                l[i], l[ind] = l[ind], l[i]
                ind += 1
                break
        for i in range((N-ind)//2):
            l[i+ind], l[N-i-1] = l[N-i-1], l[i+ind]
        return l
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(1)
```
## Geeksforgeeks
[Next Permutation](https://practice.geeksforgeeks.org/problems/next-permutation5226/1)
