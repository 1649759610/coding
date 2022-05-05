# 背包问题

有n个重量和价值分别为$w_i$和$v_i$的物品。 从这些物品中挑选出总重量不超过W的物品，求所有挑选方案中价值和的最大值。


```python
import numpy as np

def bag(w, v, n, W):
    # dp[i+1][j]: 从前i个商品中，挑选重量不超过j的物品时总价值的最大值
    # dp[0][j] = 0
    # dp[i+1][j] = dp[i][j], if j<w[i]
    # dp[i+1][j] = max(dp[i][j], dp[i][j-w[i]]+v[i])  其他
    dp = np.zeros(shape=(n+1, W+1))
    for i in range(0, n):
        for j in range(W+1):
            if j < w[i]:
                dp[i+1][j] = dp[i][j]
            else:
                dp[i+1][j] = max(dp[i][j], dp[i][j-w[i]]+v[i])

    print(dp)


if __name__ == '__main__':
    n, W=4, 5
    w, v = [2, 1, 3, 2], [3, 2, 4, 2]
    bag(w, v, n, W)

```
