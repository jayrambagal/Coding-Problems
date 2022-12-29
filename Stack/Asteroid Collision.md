## Asteroid Collision
```
We are given an integer array asteroids of size N representing asteroids in a row. For each asteroid, the absolute value represents its size, 
and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.
Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are of same size, 
both will explode. Two asteroids moving in the same direction will never meet.
```

#### Example
```bash
Input:
N = 3
asteroids[ ] = {3, 5, -3}
Output: {3, 5}
Explanation: The asteroid 5 and -3 collide resulting in 5. The 5 and 3 never collide.

Input:
N = 2
asteroids[ ] = {10, -10}
Output: { }
Explanation: The asteroid -10 and 10 collide exploding each other.

```
### Solution 

```python
class Solution:
    
    def asteroidCollision(self, N, ast):
        
        stack = []
        
        for i in ast:
            
            if not stack:
                stack.append(i)
                
            elif stack[-1] > 0 and i < 0:
                if stack[-1] > abs(i):
                    continue
                elif stack[-1] == abs(i):
                    stack.pop()
                else:
                    c = 0
                    while stack and stack[-1] > 0 and stack[-1] <= abs(i):
                        if stack[-1] == abs(i):
                            stack.pop()
                            c = 1
                            break
                        stack.pop()
                    if c:
                        continue
                    if not stack or stack[-1] < 0:
                        stack.append(i)
                        
            else:
                stack.append(i)
                
        return stack
        
```
### Complexity
```bash
Time Complexity = O(n)
Space Complexity = O(n) 
```

## Leetcode       
[Asteroid Collision](https://practice.geeksforgeeks.org/problems/asteroid-collision/1)
