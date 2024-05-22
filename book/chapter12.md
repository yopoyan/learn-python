
# 函数的定义和作用

Python 中的函数（Function）就是用来定义可重复的代码块的解决方案，函数能让我们能抽象出通用的逻辑，更好的组织和管理代码。


```scheme


def 函数名(参数1, 参数2, ...):
    函数体
    return 返回值


```

### 函数的参数


#### 没有参数的函数

```scheme

def add():
  return 1 + 2

```

#### 带参数的函数

```scheme

def login(user):
    if user == "xiaoming":
        return "登录成功"
    else:
        return "登录失败"


```

Python 中还允许函数的参数拥有默认值:带默认值的参数必须放在不带默认值的参数之后

```scheme

def login(user="xiaoming"):
    if user == "xiaoming":
        return "登录成功"
    else:
        return "登录失败"

```

#### 可变参数之 *args

*args 是 Python 中的一个特殊语法，允许你在调用函数时使用位置参数的形式传递任意数量的参数。这些参数在函数内部被收集为一个名为 args 的元组，其中包含了所有传递的位置参数。

```scheme

# 用星号表达式来表示 args 可以接收 0 个或任意多个参数
def add(*args):
    total = 0
    # 可变参数可以放在 for 循环中取出每个参数的值
    for val in args:
        if type(val) in (int, float):
            total += val
    return total


# 在调用 add 函数时可以传入 0 个或任意多个参数
print(add())
print(add(1))
print(add(1, 2))
print(add(1, 2, 3))

```

#### 可变参数之 **kwargs

**kwargs 是 Python 中的一个特殊语法，它允许你在调用函数时使用关键字参数的形式传递任意数量的参数。这些参数在函数内部被收集为一个名为 kwargs 的字典，其中键是参数名，值是参数值。

```scheme

def my_function(**kwargs):
    for key, value in kwargs.items():
        print(f"{key} = {value}")

my_function(name="John", age=30, city="New York")

# name = John
# age = 30
# city = New York


```

### Python 的内置函数

### Python 函数装饰器

在 Python 中，装饰器（Decorator）是一种特殊的函数，它可以在不修改被装饰函数源代码的情况下，为函数添加额外的功能。装饰器可以理解为是一个包装器，它将被装饰函数包裹在内部，并且可以在被装饰函数执行前后执行一些额外的操作。


我们定义一个装饰器函数 execute_time_decorator()，它的作用是在被装饰函数执行前后分别输出时间：

```scheme

import datetime

def execute_time_decorator(func):
  def wrapper():
    print("执行开始：", datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"))
    func()
    print("执行结束：", datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"))

  return wrapper


```

我们定义了一个名为 execute_time_decorator() 的装饰器函数，它接受一个函数作为参数，并返回一个内部函数 wrapper()。在 wrapper() 函数中，我们先输出一条信息表示函数即将执行，然后调用被装饰函数 func()，最后输出一条信息表示函数执行完成。

```scheme

import datetime

def execute_time_decorator(func):
  def wrapper():
    print("执行开始：", datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"))
    func()
    print("执行结束：", datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"))
  return wrapper

@execute_time_decorator
def hello():
    print("Hello, world!")

hello()
# 执行开始： 2023-05-23 15:32:52
# Hello, world!
# 执行结束： 2023-05-23 15:32:52

```

### 高阶函数

#### map 函数

map 函数可以将一个函数应用到一个序列的每个元素上，并返回一个新的序列，语法如下：

```scheme

map(function, iterable, ...)

# function 是要应用的函数，iterable 是要处理的可迭代序列

```

```scheme

numbers = [1, 2, 3, 4, 5]
def get_square(x):
  return x**2
squares = map(get_square, numbers)
print(list(squares)) # [1, 4, 9, 16, 25]


```

### reduce 函数

reduce 可以对一个序列进行累积计算，返回一个单一的结果，语法如下：
reduce(function, iterable[, initializer])

其中，function 是要应用的函数，iterable 是要处理的可迭代序列，initializer 是可选的初始值。


```scheme

from functools import reduce
def get_product(x, y):
  return x * y
numbers = [1, 2, 3, 4, 5]
product = reduce(get_product, numbers)
print(product) # 120  1 * 2 * 3 * 4 * 5

```

### filter 函数

filter 函数可以根据一个函数的返回值为 True 或者 False 来过滤一个序列（返回值为 True 的元素被保留），返回一个新的序列，语法如下：
filter(function, iterable)

```scheme

def get_even_numbers(x):
  return x % 2 == 0
numbers = [1, 2, 3, 4, 5]
evens = filter(get_even_numbers, numbers)
print(list(evens)) 
# [2, 4]

```

### lambda 函数

在使用函数的时候，如果作为参数或者返回值的函数本身非常简单，一行代码就能够完成，那么我们可以使用Lambda 函数来表示。Python 中的 Lambda 函数是没有的名字函数，所以很多人也把它叫做匿名函数，匿名函数只能有一行代码，代码中的表达式产生的运算结果就是这个匿名函数的返回值。


lambda arguments: expression

其中，lambda 是关键字，arguments 是函数的参数，expression 是函数的返回值。lambda 函数可以有任意数量的参数，但只能有一个表达式。

```scheme

sum_nums = lambda x, y: x + y
print(sum_nums(2, 3))  # 输出 5


numbers = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x**2, numbers))
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(squares)  # 输出 [1, 4, 9, 16, 25]
print(evens)  # 输出 [2, 4]

```