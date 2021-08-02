# 找到数组中第k大的数字

```python
def partition(nums, start, end):
    pivote = nums[start]
    i,j=start, end
    while i!=j:
        while i<j and nums[j]>pivote:
            j-=1
        while i<j and nums[i]<=pivote:
            i+=1
        nums[i], nums[j] = nums[j], nums[i]

    nums[start] = nums[i]
    nums[i]=pivote
    return i


def find_kmax_in_array(nums, start, end, k):
    if start > end:
        return
    wanted_index = len(nums)-k
    pivoted_index = partition(nums, start, end)

    if pivoted_index == wanted_index:
        print(nums[pivoted_index])
        return
    elif pivoted_index < wanted_index:
        find_kmax_in_array(nums, pivoted_index+1, end, k)
    else:
        find_kmax_in_array(nums, start, pivoted_index-1, k)


if __name__ == '__main__':
    a = [5,3,1,4,2]
    find_kmax_in_array(a, 0, len(a) - 1, 2)
    print(sorted(a))
    # print(a)

```
