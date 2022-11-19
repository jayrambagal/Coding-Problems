## First negative integer in every window of size k

Given an array A[] of size N and a positive integer K, find the first negative integer for each and every window(contiguous subarray) of size K.

#### Example
```bash
Input : 
N = 5
A[] = {-8, 2, 3, -6, 10}
K = 2
Output : 
-8 0 -6 -6
Explanation :
First negative integer for each window of size k
{-8, 2} = -8
{2, 3} = 0 (does not contain a negative integer)
{3, -6} = -6
{-6, 10} = -6

```
### Solution 

```python
def printFirstNegativeInteger( A, N, K):
    i=0
    j=0
    l=[]
    ans=[]
    while(j<N):
        if(A[j]<0):
            l.append(A[j])
        if(j-i+1)<K:
            j+=1
        elif(j-i+1)==K:
            if(len(l)==0):
                ans.append(0)
            else:
                ans.append(l[0])
                if l[0]==A[i]:
                    l.remove(l[0])
            j+=1
            i+=1
    return ans
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(k) 
```

## Leetcode       
[First negative integer in every window of size k](https://practice.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)
