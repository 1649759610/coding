# 中序遍历

```python

class Node(object):
    def __init__(self, val):
        self.val = val
        self.lchild = None
        self.rchild = None

class Tree(object):

    # 中序递归遍历
    def inOrderTraveral(self, root):
        if not root:
            return

        self.inOrderTraveral(root.lchild)
        print(root.val, end=" ")
        self.inOrderTraveral(root.rchild)

    # 中序非递归遍历
    def inOrderTraveralwithStack(self, root):

        stack = []
        node = root
        while node or len(stack)!=0:
            while node:
                stack.append(node)
                node = node.lchild

            if len(stack) != 0:
                node = stack.pop()
                print(node.val, end=" ")
                node = node.rchild

```
