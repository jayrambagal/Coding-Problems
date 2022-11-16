## Substrings of length k with k-1 distinct elements
Given a String S consisting only lowercase alphabets and an integer K. 

Find the count of all substrings of length K which have exactly K-1 distinct characters.

## Example 
```bash
Input:
S = "aabab"
K = 3
Output :
3
Explanation:
Possible substrings of length K = 3 are
aab : 2 distinct characters
aba : 2 distinct characters
bab : 2 distinct characters.
All of these Substrings are a possible answer,
so the count is 3.
```


## Solution
```python
#User function Template for python3

class Solution:
    
    def countOfSubstrings(self, strr, k):
        
        N = len(strr)
 
        answer = 0
    
        mapp = {}
    
        for i in range(K):
     
            try:
                mapp[strr[i]]+=1
            except:
                mapp[strr[i]]=1
             
        if (len(mapp) == K-1):
            answer += 1
    
        for i in range(K, N):
    
            try:
                mapp[strr[i]]+=1
            except:
                mapp[strr[i]]=1
             
            mapp[strr[i - K]] -= 1
    
            if (mapp[strr[i - K]] == 0):
                del mapp[strr[i - K]]
     
            if (len(mapp) == K-1):
                answer += 1
    
        return answer
    
            

#{ 
 # Driver Code Starts
#Initial Template for Python 3

if __name__ == '__main__': 
    t = int (input ())
    for _ in range (t):
        S=input()
        K=int(input())
        
        ob = Solution()
        print(ob.countOfSubstrings(S,K))
# } Driver Code Ends
 ```
#### Complexity
```bash
Time Complexity :O(n)
Space Complexity : O(n)
```

## Geeksforgeeks
[Substrings of length k with k-1 distinct elements](https://practice.geeksforgeeks.org/problems/substrings-of-length-k-with-k-1-distinct-elements/1?page=2&difficulty[]=1&difficulty[]=2&status[]=unsolved&category[]=Strings&sortBy=submissions)
