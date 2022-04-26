# 实现加法

不使用运算+和-，计算两个整数a、b之和。

```python

class Solution:
    def getSum(self, a: int, b: int) -> int:
        mask = 0xFFFFFFFF

        while b & mask != 0:
            # 对应位进位值的计算
            carry = (a & b) << 1
            # 对应位原位值的计算
            a = a ^ b
            b = carry
        
        if b > mask:
            return a & mask
        else:
            return a

```
