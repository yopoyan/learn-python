
# Python 分支

在 Python 中，要构造分支结构可以使用if、elif和 else关键字。


### if 语句

```scheme

"""
用户身份验证
"""
username = 'admin'
if username == 'admin':
    print('注意，这位是 admin 用户！')

print(username)


```

Python 中使用了缩进的方式来表示代码的层次结构，缩进可以使用任意数量的空格，但通常使用 4 个空格。

另外 if 以及 elif 和 else关键字的最后面都有一个:冒号

### if-else 语句

```scheme

username = 'admin'
password = '123456'
# 用户名是 admin 且密码是 123456 则身份验证成功否则身份验证失败
if username == 'admin' and password == '123456':
    print('身份验证成功!')
else:
    print('身份验证失败!')

```

### if-elif-else 语句

```scheme

"""
分段函数求值
"""
x = -5
if x > 1:
    y = 3 * x - 5
elif x >= -1:
    y = x + 2
else:
    y = 5 * x + 3
print(f'f({x}) = {y}')


```