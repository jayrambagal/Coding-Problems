## Job Sequencing Problem
Given a set of N jobs where each jobi has a deadline and profit associated with it.

Each job takes 1 unit of time to complete and only one job can be scheduled at a time. 

We earn the profit associated with job if and only if the job is completed by its deadline.

Find the number of jobs done and the maximum profit.

Note: Jobs will be given in the form (Jobid, Deadline, Profit) associated with that Job.

## Example 
```bash
Input:
N = 4
Jobs = {(1,4,20),(2,1,10),(3,1,40),(4,1,30)}
Output:
2 60
Explanation:
Job1 and Job3 can be done with
maximum profit of 60 (20+40).

```

## Solution 

```python
class Solution:
    
    #Function to find the maximum profit and the number of jobs done.
    def JobScheduling(self,jobs,n):
        
        jobs.sort(key=lambda x:x.profit,reverse=True)
        
        done=[0]*(101)
        profit=0
        count=0

        for i in range(n):
            
            dead=jobs[i].deadline
            serial=jobs[i].id
            cost=jobs[i].profit
            
            for j in range(dead,0,-1):
                
                if(done[j]==0):
                    done[j]=serial
                    profit+=cost
                    count+=1
                    break
                
        return (count,profit)
 ```
#### Complexity
```bash
Time Complexity :O(n*n)
Space Complexity : O(n)
```
## Geeksforgeeks
[Job Sequencing Problem](https://practice.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1?page=1&difficulty[]=1&status[]=unsolved&category[]=Strings&category[]=Dynamic%20Programming&sortBy=submissions)
