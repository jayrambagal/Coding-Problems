## Modified Numbers and Queries
Find the sum of all the numbers between the range l and r. Here each number is represented by the sum of its prime factors. 
Note : For example, 6 is represented by 5 because 6 has two prime factors 2 and 3 and 2 + 3 = 5.

## Example 
```bash
Input: l = 1, r = 2
Output: 3
Explanation: 1->1, 2->2 and 1+2=3. 

Input: l = 1, r = 6
Output: 18
Explanation: 1->1, 2->2, 3->3, 4->2
5->5, 6->2+3=5, 1+2+3+2+5+5 = 18. 

```

## Solution 

```python
class Solution:
	def sumOfAll(self, l, r):
	    
	    isprime = [True]*(r+1)
	    
	    for i in range(2,r+1):
	        for j in range(i*i,r+1,i):
	            isprime[j] = False
	    
	    ans = 0
	    while(l<=r):
	        
	        if l == 1:
	            l+=1
	            ans+=1
	            continue
	        curr = 0
	        for i in range(2,l+1):
	            if isprime[i] and l%i==0:
	                curr+=i
	        ans+=curr
	        l+=1
	        
	    return ans
 ```
#### Complexity
```bash
Time Complexity :O()
Space Complexity : O()
```


## Solution 

```python
class Solution:
	def sumOfAll(self, l, r):
		# code here
        arr=[0]*(r+1)
        arr[1]=1
        
        for i in range(2,r+1):
            if arr[i]!=0:
                continue
        
            for j in range(i,r+1,i):
                if j%i==0:
                    arr[j]+=i
        
        count=0
        
        for i in range(l,r+1):
            count+=arr[i]
        
        return count
 ```
#### Complexity
```bash
Time Complexity :O(r^2)
Space Complexity : O(r)
```
## Geeksforgeeks
[Modified Numbers and Queries](https://practice.geeksforgeeks.org/problems/modified-numbers-and-queries0904/1)
