# 位1的个数(第191题)

编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为汉明重量）。


```python
# 解法1： 循环和位移动
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        for i in range(32):
            if n & (1 << i):
                count += 1
        
        return count

# 解法2： 不去检测整数的每一位，而是依次将最低且值为1的比特位翻转为0，并增加计数器。当执行结果使整数为0时，该整数不再包含任何为1的比特，返回计数器的值
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        while n:
            count += 1
            n &= (n-1)
        
        return count

```
