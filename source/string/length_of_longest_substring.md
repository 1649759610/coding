# 无重复字符串的最长子串（第3题）


给定一个字符串 s ，请你找出其中不含有重复字符的 最长子串 的长度。

**示例 1:**  

输入: s = "abcabcbb"  
输出: 3   
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:

        max_len = 0

        for left in range(len(s)):
            right = left
            visited = set()
            
            while right < len(s):
                if s[right] not in visited:
                    visited.add(s[right])
                    right += 1
                else:
                    break

            max_len = max(max_len, len(visited))
        
        return max_len
```
