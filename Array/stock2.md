# 2. 买卖股票的最佳时机 II

![](../.gitbook/assets/image%20%2811%29.png)

![](../.gitbook/assets/image%20%289%29%20%281%29.png)

```python
import numpy as np

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        # dp[i][0] 代表第i天手上没有股票的最大利润
        # dp[i][1] 代表第i天手上有股票的最大利润
        dp = np.zeros([len(prices), 2],dtype=int)
        # 初始化
        dp[0,0] = 0
        dp[0,1] = -prices[0]

        for i in range(1, len(prices)):
            dp[i, 0] = max(dp[i-1, 0], dp[i-1, 1]+prices[i])
            dp[i, 1] = max(dp[i-1, 1], dp[i-1, 0]-prices[i])
        
        return int(max(dp[len(prices)-1]))
```

