# 模块
在 Python 中，模块（Module）是指一个包含 Python 代码的文件，可以包含函数、变量和类（后面我们会学到）等等有组织的内容。一般来说，我们会把描述一个完整功能的代码封装在一起，形成一个模块。模块可以被其他 Python 程序导入和使用，从而实现代码的复用，这就是模块化编程。


```scheme

# calucator.py
# 加法
def add(a, b):
    return a + b
# 减法
def sub(a, b):
    return a - b
# 乘法
def mul(a, b):
    return a * b
# 除法
def div(a, b):
    if b == 0:
        return "Error: divided by zero"
    else:
        return a / b

# main.py
import calculator

result1 = calculator.add(3, 5)
result2 = calculator.sub(7, 2)

print(result1) # 输出 8
print(result2) # 输出 5

```

### import 方式

```scheme

from calculator import add

result1 = calculator.add(3, 5)
print(result1)

```

### Python 内置模块


os	提供了与操作系统交互的一些函数，例如文件、目录操作等
sys	提供了与 Python 解释器交互的一些函数，例如用于退出程序的 exit() 函数
math	提供了数学函数，例如平方、立方、三角函数、指数函数等
random	提供了生成随机数的函数。
time	提供了一些关于时间操作的函数，比如返回当前时间，使用程序睡眠一定时间等。
datetime	提供了日期和时间处理的函数，比如日期加减、时区转换等
re	提供了正则表达式的支持
json	提供了 JSON 格式的编码和解码功能
statistics	提供了众多统计函数

#### random

```scheme

import random
# 生成一个 [0, 1) 范围内的随机浮点数
print(random.random())
# 生成0-9之间的随机整数
print(random.randrange(10))
# 生成一个 [1, 10] 范围内的随机整数
print(random.randint(1, 10))

lst = [1, 2, 3, 4, 5, 6, 7, 8, 9]
# 从 lst 中随机选择一个元素
print(random.choice(lst))

```

#### math

```scheme

import math

# 返回不小于 x 的最小整数
print(math.ceil(3.14))
# 返回不大于 x 的最大整数
print(math.floor(3.14))
# 返回 x 的绝对值
print(math.fabs(-3.14))
# 返回 x 的平方根
print(math.sqrt(9))

```

#### time

```scheme

import time
now = time.time()
print(now)
print('准备 sleep')
print(time.sleep(5)) # 这一步会让程序阻塞 5s 才继续执行下面的代码
print('sleep 结束')

```

#### datetime

datetime 模块中比较侧重时间和日期的运算以及格式化，所以我们主要介绍以下几个：

    now(tz=None)：返回当前的本地日期和时间，该函数会返回一个 datetime 对象。
    utcnow()：返回当前的 UTC 日期和时间，该函数会返回一个 datetime 对象。
    strftime(format)：datetime 对象中的方法，用来将 datetime 对象格式化为指定的字符串格式。
    strptime(date_string, format)：将字符串按照指定的格式转换为 datetime 对象。
    fromtimestamp(secs)：将Unix时间戳转换为 datetime 对象。
    date()：返回 datetime 对象的日期部分。
    time()：返回 datetime 对象的时间部分。
    timedelta()：表示两个日期或时间之间的差异。


```scheme

import time
# 注意 datetime 的导入方式
from datetime import datetime

local_now = datetime.now() # 返回本地时间的 datetime 对象
utc_now = datetime.utcnow()
local_now_str = local_now.strftime('%Y-%m-%d %H:%M:%S')
print(local_now_str) # 2023-05-25 15:52:11

# 将字符串转换成 datetime 对象
local_now_2 = datetime.strptime(local_now_str, '%Y-%m-%d %H:%M:%S')
print(local_now_2)

timestamp = time.time()
# 将时间戳转换为 datetime 对象
dt = datetime.fromtimestamp(timestamp)
print(dt)

```

#### datetime 时间运算

datetime 对象是可以做减法来计算时间间隔的，两个 datetime 对象相减得到一个 timedelta 对象；datetime 和 timedelta 对象相互加减，可以的得另外一个全新的 datetime 对象。timedelta 是 datetime 库 中的一个类，用于表示时间间隔，可以用来进行时间的加减操作。timedelta 类的实例可以通过 datetime 模块的 timedelta() 函数创建，其构造方法如下：

```scheme

datetime.timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, minutes=0, hours=0, weeks=0)


from datetime import datetime, timedelta

# 当前时间
now = datetime.now()
# 10 天后的时间
ten_days_later = now + timedelta(days=10)
print(ten_days_later)
# 1 小时前的时间
one_hour_ago = now - timedelta(hours=1)
print(one_hour_ago)

```


```scheme

from datetime import datetime

# 两个 datetime 对象
date1 = datetime(2021, 7, 1, 0, 0, 0)
date2 = datetime(2021, 6, 1, 0, 0, 0)
# 计算它们之间的时间差
time_diff = date1 - date2
# 输出时间差的天数和秒数
print(time_diff.days, time_diff.seconds)

```


查询 Python 的官方文档，里面有对每个模块的详细使用说明。[链接在这里。](https://docs.python.org/zh-cn/3/tutorial/stdlib.html)