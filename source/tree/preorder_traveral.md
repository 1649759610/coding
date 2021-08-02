# 前序遍历

```python

class Node(object):
    def __init__(self, val):
        self.val = val
        self.lchild = None
        self.rchild = None

class Tree(object):

    # 前序递归遍历
    def preOrderTraveral(self, root):
        if not root:
            return

        print(root.val, end=' ')
        self.preOrderTraveral(root.lchild)
        self.preOrderTraveral(root.rchild)

    # 前序非递归遍历
    def preOrderTraveralwithStack(self, root):

        stack = [root]

        while len(stack) != 0:
            node = stack.pop()
            print(node.val, end=" ")
            if node.rchild:
                stack.append(node.rchild)
            if node.lchild:
                stack.append(node.lchild)

    # 前序非递归遍历2
    def preOrderTraveralwithStack2(self, root):
        stack = []
        node = root
        while node or len(stack) != 0:
            while node:
                print(node.val, end=" ")
                stack.append(node)
                node = node.lchild

            if len(stack) != 0:
                node = stack.pop()
                node = node.rchild

```
