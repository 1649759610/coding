# 分发糖果（第135题）

n 个孩子站成一排。给你一个整数数组 ratings 表示每个孩子的评分。

你需要按照以下要求，给这些孩子分发糖果：

每个孩子至少分配到 1 个糖果。
相邻两个孩子评分更高的孩子会获得更多的糖果。
请你给每个孩子分发糖果，计算并返回需要准备的 最少糖果数目 。

 

**示例 1**：  

输入：ratings = [1,0,2]  
输出：5  
解释：你可以分别给第一个、第二个、第三个孩子分发 2、1、2 颗糖果。  

**示例 2**：  

输入：ratings = [1,2,2]  
输出：4  
解释：你可以分别给第一个、第二个、第三个孩子分发 1、2、1 颗糖果。
     第三个孩子只得到 1 颗糖果，这满足题面中的两个条件。
 

```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        ans = 0
        
        # 从左到右看需要多少糖果
        left  = [1]*len(ratings)
        for i in range(1, len(ratings)):
            if ratings[i] > ratings[i-1]:
                left[i] = left[i-1]+1
            else:
                left[i] = 1
        
        # 从右到做看需要多少糖果
        right = [1] * len(ratings)
        for i in range(len(ratings)-2, -1, -1):
            if ratings[i] > ratings[i+1]:
                right[i] = right[i+1] + 1
            else:
                right[i] = 1
        
        # 合并以上结果
        for i in range(len(ratings)):
            ans += max(left[i], right[i])

        return ans




```
