## IPL 2021 - Match Day 2

Due to the rise of covid-19 cases in India, this year BCCI decided to organize knock-out matches in IPL rather than a league.

Today is matchday 2 and it is between the most loved team Chennai Super Kings and the most underrated team - Punjab Kings. 

Stephen Fleming, the head coach of CSK, analyzing the batting stats of Punjab. He has stats of runs scored by all N players 

in the previous season and he wants to find the maximum score for each and every contiguous sub-list of size K to strategize for the game.

#### Example
```bash
Input:
N = 9, K = 3
arr[] = 1 2 3 1 4 5 2 3 6
Output: 
3 3 4 5 5 5 6 
Explanation: 
1st contiguous subarray = {1 2 3} Max = 3
2nd contiguous subarray = {2 3 1} Max = 3
3rd contiguous subarray = {3 1 4} Max = 4
4th contiguous subarray = {1 4 5} Max = 5
5th contiguous subarray = {4 5 2} Max = 5
6th contiguous subarray = {5 2 3} Max = 5
7th contiguous subarray = {2 3 6} Max = 6

```
### Solution 

```python

 
class Solution:
    def max_of_subarrays(self,arr,n,k):
        ans = []
        temp =[]
        j = 0
        for i in range(k):
            j = i
            temp.append(arr[i])
            
        j = j+1
        maxx = 0
        while j < n:
            maxx = max(temp)
            ans.append(maxx)
            temp.pop(0)
            temp.append(arr[j])
            j+=1
        temp.pop(0)
        temp.append(arr[n-1])
        maxx = max(temp)
        ans.append(maxx)
        return ans
                   
```
### Complexity
```bash
Time Complexity = O()
Space Complexity = O() 
```
### Solution 

```python
#User function Template for python3

class Solution:
    def max_of_subarrays(self,arr,n,k):
        dq = []
        ans = []
        
        for i in range(n):
            while dq and dq[0] == i-k:
                dq.pop(0)
                
            while dq and arr[dq[-1]]<arr[i]:
                dq.pop(-1)
            dq.append(i)
            
            if i>=k-1 :
                ans.append(arr[dq[0]])
                
        return ans
        
```
### Complexity
```bash
Time Complexity = O(n)+O(n)
Space Complexity = O(k) 
```

## Leetcode       
[IPL 2021 - Match Day 2](https://practice.geeksforgeeks.org/problems/deee0e8cf9910e7219f663c18d6d640ea0b87f87/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
