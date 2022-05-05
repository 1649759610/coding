# 回文数（第9题）

给你一个整数 x ，如果 x 是一个回文整数，返回 true ；否则，返回 false 。

回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

例如，121 是回文，而 123 不是。
 

**示例 1**：  
输入：x = 121   
输出：true  


**示例 2**：  
输入：x = -121  
输出：false  
解释：从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。


```python

class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False

        tmp_x = x
        y = 0
        while tmp_x != 0:
            y = y*10 + (tmp_x % 10)
            tmp_x = tmp_x // 10
        
        return y==x



```
