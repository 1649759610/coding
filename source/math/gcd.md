# 最大公约数

两个整数的最大公约数等于其中较小的那个数和两数相除余数的最大公约数，我们可以通过递归，不断缩小这个数，直到某个数字为0，则另一个数字为最大公约数。

```python
# 最大公约数

def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)

a = 27
b = 18
gcd(a, b)
```
