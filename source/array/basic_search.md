# 全搜索

```python

result = []
def dfs(nums, i, result):
    if i==len(nums):
        print(result)
        return

    dfs(nums, i+1, result)

    result.append(nums[i])
    dfs(nums, i+1, result)
    result.pop()


if __name__ == '__main__':
    nums = [1,2,3]
    dfs(nums, 0, result)


```
