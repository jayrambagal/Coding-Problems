## Stock span problem
```
The stock span problem is a financial problem where we have a series of n daily price quotes for a stock and we need 
to calculate the span of stocks price for all n days. 
The span Si of the stocks price on a given day i is defined as the maximum number of consecutive days just before 
the given day, for which the price of the stock on the current day is less than or equal to its price on the given day.
For example, if an array of 7 days prices is given as {100, 80, 60, 70, 60, 75, 85}, then the span values for corresponding 
7 days are {1, 1, 1, 2, 1, 4, 6}.
```
## Example 
```bash
Input: 
N = 7, price[] = [100 80 60 70 60 75 85]
Output:
1 1 1 2 1 4 6
Explanation:
Traversing the given input span for 100 
will be 1, 80 is smaller than 100 so the 
span is 1, 60 is smaller than 80 so the 
span is 1, 70 is greater than 60 so the 
span is 2 and so on. Hence the output will 
be 1 1 1 2 1 4 6.

```


## Solution (brut)
```python
class Solution:
    def calculateSpan(self,a,n):
        
        ans = [1]
        
        for i in range(1,n):
            count = 1
            if i-1 >= 0:
                if a[i] >= a[i-1]:
                    for j in range(i-1,-1,-1):
                        if a[i]>=a[j]:
                            count+=1
                        else:
                            break
            ans.append(count)
            
        return ans
```
#### Complexity
```bash
Time Complexity :O(n^2) 
Space Complexity : O()

```

## Geeksforgeeks
[Stock span problem](https://practice.geeksforgeeks.org/problems/stock-span-problem-1587115621/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Arrays&sortBy=submissions)
