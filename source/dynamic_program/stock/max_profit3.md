# 最佳买卖股票时机含冷冻期(第309题)

给定一个整数数组prices，其中第  prices[i] 表示第 i 天的股票价格 。​

设计一个算法计算出最大利润。在满足以下约束条件下，你可以尽可能地完成更多的交易（多次买卖一支股票）:

卖出股票后，你无法在第二天买入股票 (即冷冻期为 1 天)。
注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。

 

**示例 1**:
输入: prices = [1,2,3,0,2]  
输出: 3   
解释: 对应的交易状态为: [买入, 卖出, 冷冻期, 买入, 卖出]  

**示例 2**:  
输入: prices = [1]  
输出: 0  


```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices)<=1:
            return 0

        buy = [0] * len(prices)
        sell = [0] * len(prices)

        # 处理第1天
        buy[0] = -prices[0]
        sell[0] = 0

        # 处理第2天
        buy[1] = max(buy[0], sell[0]-prices[1])
        sell[1] = max(sell[0], buy[0]+prices[1])

        for i in range(2, len(prices)):
            buy[i] = max(sell[i-2]-prices[i], buy[i-1])
            sell[i] = max(buy[i-1]+prices[i], sell[i-1])
        
        return sell[-1]



```
