# 爬楼梯（第70题）

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？



**示例 1**：   
输入：n = 2  
输出：2  
解释：有两种方法可以爬到楼顶。  
1. 1 阶 + 1 阶  
2. 2 阶  


**示例 2**：
输入：n = 3  
输出：3  
解释：有三种方法可以爬到楼顶。  
1. 1 阶 + 1 阶 + 1 阶  
2. 1 阶 + 2 阶  
3. 2 阶 + 1 阶  


```python
# 解法 1
import numpy as np

class Solution:
    def climbStairs(self, n: int) -> int:
        # dp[i]: 到第i个阶梯的走法数量
        if n == 1:
            return 1
        if n == 2:
            return 2

        dp = np.zeros(shape=(n,), dtype=int)
        dp[0] = 1
        dp[1] = 2
        for i in range(2, n):
            dp[i] = dp[i-1] + dp[i-2]
        # print(dp)

        return int(dp[-1])


# 解法2： 空间优化
import numpy as np

class Solution:
    def climbStairs(self, n: int) -> int:
        # dp[i]: 到第i个阶梯的走法数量
        if n == 1:
            return 1
        if n == 2:
            return 2

        dp = np.zeros(shape=(n,), dtype=int)
        dp[0] = 1
        dp[1] = 2
        first, sencond = 1, 2
        for i in range(2, n):
            tmp = sencond
            sencond = first + sencond
            first = tmp

        return sencond


# 解法3： 递归
import numpy as np

class Solution:
    def climbStairs(self, n: int) -> int:

        def helper(n):
            # dp[i]: 到第i个阶梯的走法数量
            if n == 1:
                return 1
            if n == 2:
                return 2
            
            return helper(n-1)+helper(n-2)
        
        return helper(n)





```
