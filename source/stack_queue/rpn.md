# 逆波兰表达式

逆波兰表达式是一种后缀表达式，所谓后缀就是指算符写在后面。

平常使用的算式则是一种中缀表达式，如 ( 1 + 2 ) * ( 3 + 4 ) 。
该算式的逆波兰表达式写法为 ( ( 1 2 + ) ( 3 4 + ) * ) 。
逆波兰表达式主要有以下两个优点：

去掉括号后表达式无歧义，上式即便写成 1 2 + 3 4 + * 也可以依据次序计算出正确结果。
适合用栈操作运算：遇到数字则入栈；遇到算符则取出栈顶两个数字进行计算，并将结果压入栈中。


```python 
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []

        for val in tokens:
            if val.isdigit() or (len(val)>1):
                stack.append(val)
            else:
                v1 = stack.pop()
                v2 = stack.pop()
                r = str(int(eval(v2+val+v1)))
                stack.append(r)
        
        return eval(stack[0])

```
