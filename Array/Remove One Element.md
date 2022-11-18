## Remove One Element
Alice has an array AA consisting of NN distinct integers. Bob takes exactly N - 1N−1 elements from this array and adds a positive 

integer XX (i.e. X \gt 0X>0) to each of these numbers and then shuffles them to form a new array BB of length N - 1N−1.

You are given both arrays AA and BB. You have to identify the value of XX chosen by Bob. If there are multiple possible values of XX, 

print the smallest of them. It is guaranteed that for the given input, there exists at least one possible value of XX.

Note: Since the input is large, prefer using fast input methods.

## Example 
```bash
input :
3
4
1 4 3 8
15 8 11
2
4 8
10
2
2 4
3
output :

7
2
1

```

## Solution 

```python
t = int(input())
for i in range(t):
    n = int(input())
    arr1 = list(map(int,input().split()))[:n]
    arr2 = list(map(int,input().split()))[:n-1]
    
    arr1.sort()
    arr2.sort()
    
    ans1 = arr2[0]-arr1[0]
    ans2 = arr2[0]-arr1[1]
    
    if (n>2 and arr2[1]-arr1[2]!=ans2) or ans2<=0:
        print(ans1)
    else:
        print(ans2)

 ```
#### Complexity
```bash
Time Complexity :O(nlogn) + O(nlogn)
Space Complexity : O(1)
```
## Geeksforgeeks
[Remove One Element](https://www.codechef.com/problems/REMONE?tab=statement)
