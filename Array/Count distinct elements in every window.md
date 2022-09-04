## Count distinct elements in every window
Given an array of integers and a number K. Find the count of distinct elements in every window of size K in the array.

## Example 
```bash
Input:
N = 7, K = 4
A[] = {1,2,1,3,4,2,3}
Output: 3 4 4 3
Explanation: Window 1 of size k = 4 is
1 2 1 3. Number of distinct elements in
this window are 3. 
Window 2 of size k = 4 is 2 1 3 4. Number
of distinct elements in this window are 4.
Window 3 of size k = 4 is 1 3 4 2. Number
of distinct elements in this window are 4.
Window 4 of size k = 4 is 3 4 2 3. Number
of distinct elements in this window are 3.

```

## Solution 

```python
class Solution:
    def countDistinct(self, A, N, K):
        ans = []
        res = []
        for i in range(0,(N-K)+1):
            for j in range(i,i+K):
                if A[j] not in ans:
                    ans.append(A[j])
                    
            res.append(len(ans))
            ans.clear()
        return res
 ```
#### Complexity
```bash
Time Complexity :O(n^2)
Space Complexity : O(n)
``` 
## Solution
```python
class Solution:
    def countDistinct(self, A, N, K):
        freq = {}
        ans = []
        
        for i in range(K-1):
            if A[i] in freq:
                freq[A[i]]+=1
            else:
                freq[A[i]] = 1
        i = K-1   
        j = 0
        while i<N:
            if A[i] in freq:
                freq[A[i]]+=1
                
            else:
                freq[A[i]] = 1
                
            ans.append(len(freq))
            
            if freq[A[j]] == 1:
                del freq[A[j]]
            else:
                freq[A[j]] -=1
                
            i+=1
            j+=1
            
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Count distinct elements in every window](https://practice.geeksforgeeks.org/problems/count-distinct-elements-in-every-window/1?page=1&status[]=unsolved&category[]=sliding-window&sortBy=submissions)
