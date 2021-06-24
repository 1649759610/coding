# 对称二叉树

```text
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:

        def isSym(left, right):
            if (not left) and (not right):
                return True

            if ((not left) and right) or (left and (not right)):
                return False

            if left.val != right.val:
                return False

            return isSym(left.left, right.right) and isSym(left.right, right.left)

        return isSym(root.left, root.right)
```

