# 回溯法模板

```python
# idx表示当前位置， cur表示当前路径的某个信息(例如sum)， path表示路径

def dfs(idx, cur, path):
    # 结束条件
    # 1. 找到解
    if cur == target:
        ans.append(path.copy())
        return
    # 2. 搜索完毕
    if idx == n:
        return
    
    # 考虑可能的解，进入下一层循环
    for num in nums:
        if num == error or nums in visited:
            continue
        # 更新状态
        visited.add(num)
        path.append(num)
        dfs(idx + 1, cur+num, path)
        # 恢复状态
        path.pop()
        visited.remove(num)




```
