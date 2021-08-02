# 全排列

```python
def permutation(array, n):
    if n == len(array):
        print(array)
        return

    for i in range(n, len(array)):
        array[n], array[i] = array[i], array[n]
        permutation(array, n+1)
        array[n], array[i] = array[i], array[n]

if __name__ == '__main__':    
    array = [1, 2, 3]
    permutation(array, 0)

```
