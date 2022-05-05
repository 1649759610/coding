# 二叉树中的最大路径和

路径 被定义为一条从树中任意节点出发，沿父节点-子节点连接，达到任意节点的序列。同一个节点在一条路径序列中 至多出现一次 。该路径 至少包含一个 节点，且不一定经过根节点。
​
备注：  
1） 判定路径和时，需要左子树最大和值+右子树最大和值+root值  
2） 判定当前子树对最大路径和的贡献时需要单个路径：root.val+ 左子树和右子树较大的那一项   

```python
class Solution:
    def maxPathSum(self, root):
        self.maxSum =  float("-inf")
        # helper 用来求以root为根的子树的最大路径和
        def helper(root):
            if not root:
                return 0

            maxLeft = max(helper(root.left), 0)
            maxRight = max(helper(root.right), 0)

            # 求当前路径最大值并更新
            priceNewPath = root.val + maxLeft + maxRight
            self.maxSum = max(self.maxSum, priceNewPath)

            return root.val + max(maxLeft, maxRight)
        
        helper(root)
        return self.maxSum


```
