# 层次遍历

```python

class Node(object):
    def __init__(self, val):
        self.val = val
        self.lchild = None
        self.rchild = None

class Tree(object):

    # 层次遍历
    def levelTraverl(self, root):
        queue = [root]
        while len(queue)!=0:
            node = queue.pop(0)
            print(node.val, end=" ")
            if node.lchild:
                queue.append(node.lchild)
            if node.rchild:
                queue.append(node.rchild)
```
