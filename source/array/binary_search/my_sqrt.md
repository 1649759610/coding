# X的平方根

```python
# 牛顿法
class Solution:
    def mySqrt(self, x: int) -> int:

        k = 1
        while abs(k*k - x) > 1e-9:
            k = (k + x/k)/2
        
        return k

# 二分法
class Solution:
    def mySqrt(self, x: int) -> int:

        l, r = 0, x
        mid = (l+r) / 2
        
        while abs(mid*mid - x) > 1e-9:
            mid = (l+r)/2
            if mid * mid < x:
                l = mid
            elif mid * mid > x:
                r = mid
    
        return mid


```
