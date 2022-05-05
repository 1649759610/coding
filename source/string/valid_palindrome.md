# 验证回文字符串2（第680题）

给定一个非空字符串 s，最多删除一个字符。判断是否能成为回文字符串。

 

**示例 1**:  
输入: s = "aba"  
输出: true  


**示例 2**:  
输入: s = "abca"  
输出: true  
解释: 你可以删除c字符。  

**示例 3**:  
输入: s = "abc"  
输出: false  



```python

class Solution:
    def validPalindrome(self, s: str) -> bool:
        l, r = 0, len(s)-1
        s_list = list(s)

        def validPalindrome_fn(s_list, l, r):
            while l <= r:
                if s_list[l] == s_list[r]:
                    l += 1
                    r -= 1
                else:
                    return False
        
            return True

        while l<=r:
            if s_list[l] == s_list[r]:
                    l += 1
                    r -= 1
            else:
                # 尝试左边：
                left = validPalindrome_fn(s_list, l+1, r)
                if left:
                    return True
                # 尝试右边
                right = validPalindrome_fn(s_list, l, r-1)
                
                if right:
                    return True
                else:
                    return False
                    
        return True



```
