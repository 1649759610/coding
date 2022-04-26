# 整数替换(第397题)

给定一个正整数，你可以做如下操作：

- 如果n是偶数，则用n/2替换n
- 如果n是奇数，则可以用n+1 或 n-1 替换 n

求n变为1所需的最小替换次数是多少？


```python
# 解法1：递归法
class Solution:
    def integerReplacement(self, n: int) -> int:
        def helper(n):
            if n == 1:
                return 0
            elif n % 2 == 0:
                return helper(n/2) + 1
            else:
                return min(helper(n+1), helper(n-1)) + 1
        
        return helper(n)

# 解法2： 位运算法, 一种确定性的规则如下：
# 1. 如果n是偶数，则直接n/2
# 2. 如果n是奇数，那它的二进制最低两位有两种情况：01和11
    ## 如果是01，则n-1
    ## 如果是11，则n+1
# 3. 特殊情况3，应该 -1

class Solution:
    def integerReplacement(self, n: int) -> int:
        if n<=1:
            return 0
        count = 0

        while n > 3:
            # 如果n为偶数
            if n & 1 == 0:
                n >>= 1
            # 如果n为奇数，且后两位为11
            elif n & 0x03 ==0x03:
                n += 1
            # 如果n为奇数，且后两位为01
            else:
                n -= 1
            count += 1

        return (count + 2) if n ==3 else (count + 1)

# 解法3

class Solution:
    def integerReplacement(self, n: int) -> int:
        count = 0

        while n > 1:
            # 如果n为偶数
            if n & 1 == 0:
                n >>= 1
            # 如果n为奇数
            else:
                # 如果n为奇数，且后两位为01 或特殊情况3
                if (n & 2 == 0) or n == 3:
                    n -= 1
                # 如果n为奇数，且后两位为11
                else:
                    n += 1
            count += 1

        return count

```
