## Intro

```python 
# Creating a Node
class Node:
    def __init__(self,data):
        self.left = None
        self.right = None
        self.data = data
        
    # Inserting a elements at specific position   
    
    def insert(self,data):
        if self.data == None:
            self.data = data
            
        else:
            if data <self.data:
                
                if self.left is None:
                    self.left = Node(data)
                else:
                    self.left.insert(data)
                    
            elif data > self.data:
                if self.right is None:
                    self.right = Node(data)
                    
                else:
                    self.right.insert(data)
                    
root = Node('g')
root.insert('c')
root.insert('a')
root.insert('b')
```
