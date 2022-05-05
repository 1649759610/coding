# 路径总和2 （第113题）

给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

```python

# 解法1： DFS递归
ans = []
def pathSum(root, target, path):
    if not root:
        return
    if root.left is None and root.right is None and target - root.val==0:
        path += [root.val]
        ans.append(path)
    
    pathSum(root.left, target-root.val, path + [root.val])
    pathSum(root.right, target-root.val, path + [root.val])


```
