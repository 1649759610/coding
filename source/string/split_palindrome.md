# 分割回文串

给你一个字符串 s，请你将 s 分割成一些子串，使每个子串都是 回文串 。返回 s 所有可能的分割方案。

回文串 是正着读和反着读都一样的字符串。



```python

class Solution:
    def partition(self, s: str) -> List[List[str]]:
        # 先构造回文矩阵，判断任意的s[i:j]（i>=j）是否是回文串
        n=len(s)
        f=[[True]*n for _ in range(n)]

        for i in range(n-1, -1, -1):
            for j in range(i+1, n):
                f[i][j] = f[i+1][j-1] & (s[i]==s[j])

        # 接下来执行回溯函数
        results = []
        path = []

        def dfs(i):
            if i==n:
                results.append(path[:])
                return

            for j in range(i, n):
                if f[i][j]:
                    path.append(s[i:j+1])
                    dfs(j+1)
                    path.pop()

        dfs(0)

        return results

```
