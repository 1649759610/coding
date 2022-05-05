# 任意选取n个不重复数字

```python
# 解法 1
ans = []
def fn(nums, path, idx):
    if len(path) == 2:
        ans.append(path.copy())
        return
    
    for i in range(idx, len(nums)):
        path.append(nums[i])
        fn(nums, path, i+1)
        path.pop()
    
nums = [1,2, 3, 4]
fn(nums, [], 0)
print(ans)

# 解法 2
ans = []
length = 2
def select_n_numbers(nums, path, idx):
    if len(path) == length:
        ans.append(path[:])
        return
    
    for i in range(idx, len(nums)):
        select_n_numbers(nums, path+[nums[i]], i+1)

nums = [1,2, 3, 4]
select_n_numbers(nums, [], 0)
print(ans)

```
