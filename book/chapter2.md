# 第二章 变量和类型


### 变量和基本的数据类型

在编程语言中，变量是数据的载体，简单的说就是一块用来保存数据的内存空间，变量的值可以被读取和修改。Python 中的数据类型很多，下面是常用的数据类型。

- 整型（int）：整数，顾名思义，比如 10、20、30 就是最常用的十进制整数。除此之外，还可以使用二进制、八进制、十六进制来表示整数。
- 浮点型（float）：浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的，浮点数除了数学写法（如123.456）之外还支持科学计数法（如1.23456e2）。
- 字符串型（str）：字符串是以单引号或双引号括起来的任意文本，比如'hello'和"hello"。
- 布尔型（bool）：布尔值只有True、False两种值，要么是True，要么是False。

### 变量命名

在Python 中，变量命名需要遵循以下这些规则：
- 变量名由字母、数字和下划线构成，数字不能开头。
- 大小写敏感，简单的说就是大写的A和小写的a是两个不同的变量。
- 变量名不要跟 Python 语言的关键字（有特殊含义的单词，后面会讲到）和保留字（如已有的函数、模块等的名字）发生重名的冲突。

最佳实践：变量名通常使用小写英文字母，多个单词用下划线进行连接。

### 变量赋值

将数据存储在变量里的过程我们一般称之为赋值，在 Python 中用 = 作为赋值运算符，下面通过一个例子来说明变量的类型和变量的赋值。


```scheme

age = 27                    # 将数字赋值给 age 变量
name = "Stan Xing"          # 将字符串赋值给 name 变量
print(age)
print(name)


```

### 变量和类型

在编程语言中，对不同类型的变量代表的含义和在底层机器码中表示的含义是完全不同的，在下面这个例子里，age1 和 age2 看似相同，但是含义完全不同，age1 是一个字符串类型的 27， age2 是一个整数型的 27。如果我们需要 age1 变量的值，但是希望把字符串值转换成数字，这里就要涉及到类型检查和类型转换。

```scheme

age1 = '27'
age2 = 27

```

### 变量类型检查

在 Python 中可以使用type函数对变量的类型进行检查。

```scheme

"""
使用type()检查变量的类型
"""
a = 100
b = 12.345
c = 'hello, world'
d = True
print(type(a))    # <class 'int'>
print(type(b))    # <class 'float'>
print(type(c))    # <class 'str'>
print(type(d))    # <class 'bool'>

```

### 变量类型转换

不同类型的变量可以相互转换，这一点可以通过 Python 的内置函数来实现。

- int()：将一个数值或字符串转换成整数，可以指定进制。
- float()：将一个字符串转换成浮点数。
- str()：将指定的对象转换成字符串形式，可以指定编码。
- chr()：将整数转换成该编码对应的字符串（一个字符）。
- ord()：将字符串（一个字符）转换成对应的编码（整数）。

```scheme

"""
Python中的类型转换操作
"""
a = 100
b = 12.345
c = 'hello, world'
d = True
# 整数转成浮点数
print(float(a))    # 100.0
# 浮点型转成字符串 (输出字符串时不会看到引号哟)
print(str(b))      # 12.345
# 字符串转成布尔型 (有内容的字符串都会变成True)
print(bool(c))     # True
# 布尔型转成整数 (True会转成1，False会转成0)
print(int(d))      # 1
# 将整数变成对应的字符 (97刚好对应字符表中的字母a)
print(chr(97))     # a
# 将字符转成整数 (Python中字符和字符串表示法相同)
print(ord('a'))    # 97

```