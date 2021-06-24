# 将有序数组转换为二叉搜索树

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:

        def creatBST(nums, start, end):
            if start>end:
                return 
            mid = (start+end)//2
            root = TreeNode(nums[mid])
            root.left = creatBST(nums, start, mid-1)
            root.right = creatBST(nums, mid+1, end)
            return root
        return creatBST(nums, 0, len(nums)-1)
```

