# 二叉树的最近公共祖先

给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

```python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

ans = None;
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def findAncestor(root, p, q):
            global ans
            if not root:
                return False
            
            lchild = findAncestor(root.left, p, q)
            rchild = findAncestor(root.right, p, q)

            if (lchild and rchild) or ((root.val==p.val or root.val==q.val) and (lchild or rchild)):
                ans = root
            
            return lchild or rchild or (root.val==p.val) or (root.val==q.val)

        findAncestor(root, p, q)
        return ans

```
