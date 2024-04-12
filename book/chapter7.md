
# Python 循环结构

在 Python 中构造循环结构有两种做法，一种是for-in循环，另一种是while循环。

### for-in 循环

```scheme

for x in range(0, 100):
  print('hello, world')

```

### while 循环
while 循环通过一个能够产生 bool 值的表达式来控制循环，当表达式的值为 True 时则继续循环，当表达式的值为 False 时则结束循环。


```scheme

# 计算 1 到 10 的整数之和
i = 1
total = 0
while i <= 10:
    total += i
    i += 1

print(total)


```

### break 和 continue

break 关键字，它的作用是提前结束循环。
continue，它可以用来放弃本次循环后续的代码直接让循环进入下一轮。


**如果知道循环的次数，我们通常使用for循环；如果循环次数不能确定，可以用while循环。在循环中还可以使用break来提前结束循环，也可以使用 continue 来跳过本轮循环。**