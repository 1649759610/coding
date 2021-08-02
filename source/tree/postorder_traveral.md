# 后序遍历

```python

class Node(object):
    def __init__(self, val):
        self.val = val
        self.lchild = None
        self.rchild = None

class Tree(object):

    # 后序递归遍历
    def postOrderTraveral(self, root):
        if not root:
            return

        self.postOrderTraveral(root.lchild)
        self.postOrderTraveral(root.rchild)
        print(root.val, end=" ")

    # 后序非递归遍历
    # 这个想法厉害了，前序遍历顺序为：根-左-右， 后序遍历顺序为：左-右-根
    # 可以先按照：根-右-左 进行遍历记录数值， 然后将记录的数值列表进行翻转reverse，就是: 左-右-根
    def postTraveralwithStack(self, root):
        stack = [root]
        vals = []
        while len(stack)!=0:
            node = stack.pop()
            vals.append(node.val)

            if node.lchild:
                stack.append(node.lchild)

            if node.rchild:
                stack.append(node.rchild)

        for val in reversed(vals):
            print(val, end=" ")

```
