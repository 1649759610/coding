# 创建树

```python

class Node(object):
    def __init__(self, val):
        self.val = val
        self.lchild = None
        self.rchild = None

class Tree(object):
    def __init__(self, nums):
        self.nums = nums
        self.root = self.createTree(nums)

    # 递归建立树
    def createTree(self, nums):
        root = Node(nums[0])
        for i in range(1, len(nums)):
            self._insert_tree(root, nums[i])

        return root

    # 插入节点
    def _insert_tree(self, root, val):

        if not root:
            node = Node(val)
            return node

        if val < root.val:
            root.lchild = self._insert_tree(root.lchild, val)
        if val > root.val:
            root.rchild = self._insert_tree(root.rchild, val)

        return root


```
