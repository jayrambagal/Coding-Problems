## Top k numbers in a stream
Given N numbers in an array. Your task is to keep at-most K numbers at the top (According to their frequency).  

We basically need to print top k numbers when input stream has included k distinct elements, 

else need to print all distinct elements sorted by frequency.

## Example 
```bash
Input:
N=5, K=4
arr[] = {5, 2, 1, 3, 2} 
Output: 5 2 5 1 2 5 1 2 3 5 2 1 3 5 
Explanation:
Firstly their was 5 whose frequency
is max till now. so print 5.
Then 2 , which is smaller than 5 but
their frequency is same so print 2 5.
Then 1, which is smallet among all the
number arrived, so print 1 2 5.
Then 3 , so print 1 2 3 5
Then again 2, which has the highest
frequency among all number so 2 1 3 5.

```

## Solution 

```python
class Solution:
    def kTop(self,arr, n, k):
        ans = []
        top = [0]*(k+1)
        freq = {i:0 for i in range(k+1)}
        
        for i in range(n):
            try:
                freq[arr[i]]+=1
            except:
                freq[arr[i]] = 1
            
            top[k] = arr[i]
            
            index = top.index(arr[i]) - 1
            
            while index >= 0:
                
                if freq[top[index]] < freq[top[index+1]]:
                    top[index],top[index+1] = top[index+1],top[index]
                    
                elif freq[top[index]] == freq[top[index+1]] and top[index] > top[index+1]:
                    top[index],top[index+1] = top[index+1],top[index]
                    
                else:
                    break
                
                index-=1
            
            for i in range(len(top)):
                if top[i]!=0 and i<k:
                    ans.append(top[i])
        return ans
 ```
#### Complexity
```bash
Time Complexity :O(n*k)
Space Complexity : O(n)
``` 


## Geeksforgeeks
[Top k numbers in a stream](https://practice.geeksforgeeks.org/problems/top-k-numbers3425/1?page=1&difficulty[]=1&status[]=unsolved&company[]=Amazon&category[]=Arrays&sortBy=submissions)
