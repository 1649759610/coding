# 路径总和（第112题）

给定一个二叉树和一个目标和，判断概述中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

```python
# 解法1： DFS递归
def hasPathSum(root, target):
    if not root:
        return False
    
    if root.left is None and root.right is None:
        return root.val == target
    
    return hasPathSum(root.left, target-root.val) or hasPathSum(root.right, target-root.val)


# 解法2： DFS迭代，使用非递归方式解决
def hasPathSum(root, target):
    if not root: 
        return False
    stack = [(root, target - root.val)]
    while stack:
        node, remain = stack.pop()
        if node.left is None and node.right is None and remain==0:
            return True
        if node.right:
            stack.append((node.right, remain-node.right.val))
        if node.left:
            stack.append((node.legt, remain-node.left.val))
    
    return False

```
