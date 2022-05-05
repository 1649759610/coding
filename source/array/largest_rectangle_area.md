# 柱状图中最大的矩形（第84题）

给定 n 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。

求在该柱状图中，能够勾勒出来的矩形的最大面积。




```python
# 解法1：左右端点法
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        if len(heights) == 1:
            return heights[0]

        # 左右端点法
        max_area = float("-inf")
        for i in range(len(heights)):
            max_area = max(max_area, heights[i])
            min_height = heights[i]
            for j in range(i+1, len(heights)):
                min_height = min(min_height, heights[j])
                area = min_height * (j-i+1)
                max_area = max(max_area, area)
        
        return max_area
                
# 解法2：中心扩展法
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        n = len(heights)
        l, r = [-1]*n, [n]*n
        max_area = 0

        for i in range(1, n):
            j = i - 1
            while j >= 0 and heights[j] >= heights[i]:
                j -= 1
            l[i] = j
        
        for i in range(n-2, -1, -1):
            j = i + 1
            while j < n and heights[j] >= heights[i]:
                j += 1
            r[i] = j
        
        for i in range(n):
            max_area = max(max_area, heights[i]*(r[i] - l[i] - 1))
        
        return max_area

# 优化的中心扩展法
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        n = len(heights)
        l, r = [-1]*n, [n]*n
        max_area = 0

        for i in range(1, n):
            j = i - 1
            while j >= 0 and heights[j] >= heights[i]:
                j = l[j]
            l[i] = j
        
        for i in range(n-2, -1, -1):
            j = i + 1
            while j < n and heights[j] >= heights[i]:
                j = r[j]
            r[i] = j
        
        for i in range(n):
            max_area = max(max_area, heights[i]*(r[i] - l[i] - 1))
        
        return max_area

```
