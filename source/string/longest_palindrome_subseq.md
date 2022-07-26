# 最长回文子序列（第516题）

给你一个字符串 s ，找出其中最长的回文子序列，并返回该序列的长度。

子序列定义为：不改变剩余字符顺序的情况下，删除某些字符或者不删除任何字符形成的一个序列。

 

**示例 1**：  
输入：s = "bbbab"  
输出：4  
解释：一个可能的最长回文子序列为 "bbbb" 。    

**示例 2**：  
输入：s = "cbbd"  
输出：2  
解释：一个可能的最长回文子序列为 "bb" 。  


```python
# 解法1

class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        dp = [[0]*len(s) for i in range(len(s))]

        for i in reversed(range(len(s))):
            for j in range(i, len(s)):
                if i == j:
                    dp[i][j] = 1
                elif s[i] == s[j]:
                    dp[i][j] = dp[i+1][j-1] + 2
                else:
                    dp[i][j] = max(dp[i+1][j], dp[i][j-1])
        
        return dp[0][len(s)-1]

# 解法2

class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        left, right = 0, 0
        n = len(s)
        tmp_set = set()
        max_len = 0

        while left < n and right < n:
            if s[right] not in tmp_set:
                tmp_set.add(s[right])
                max_len = max(max_len, right-left+1)
                right += 1
            else:
                while left <= right and s[left]!=s[right]:
                    tmp_set.remove(s[left])
                    left += 1
                tmp_set.remove(s[left])
                left += 1

        
        return max_len
                



```
