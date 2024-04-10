
# Python 字符串

所谓字符串，就是由零个或多个字符组成的有限序列

```scheme

s1 = 'hello, world!'
s2 = "你好，世界！"
print(s1, s2)

# 以三个双引号或单引号开头的字符串可以折行
s3 = '''
hello,
world!
'''
print(s3, end='')


Result:
hello, world! 你好，世界！

hello,
world!


```

### 转义字符和原始字符串

在字符串中可以使用\（反斜杠）来表示转义，也就是说\后面的字符不再是它原来的意义，例如：\n不是代表反斜杠和字符n，而是表示换行符；\t也不是代表反斜杠和字符t，而是表示制表符。

#### 原始字符串的输出
Python 中的字符串可以r或R开头，这种字符串被称为原始字符串，意思是字符串中的每个字符都是它本来的含义，没有所谓的转义字符。

```scheme

# 字符串s1中\t是制表符，\n是换行符
s1 = '\time up \now'
print(s1)
# 字符串s2中没有转义字符，每个字符都是原始含义
s2 = r'\time up \now'
print(s2)

```

### 格式化字符串

#### format 方法

```scheme

在字符串中使用{}作为占位符，并调用format方法，依次传入变量值，最后返回新的字符串。

name = 'xiaoming'
age = 18
print('My name is {}, I am {} years old.'.format(name, age)) 

```

#### f-strings 表示法
f-string的语法更加简洁，只需要在字符串前加上 f，然后在大括号 {} 中使用变量名即可

```scheme

name = 'xiaoming'
age = 18
print(f'My name is {name}, I am {age} years old.') 

```

### 字符串运算
Python 为字符串类型提供了非常丰富的运算符。

#### 字符串拼接

使用+和*运算符来实现字符串的拼接和重复操作。

```scheme

s1 = 'hello' + ' ' + 'world'
print(s1)    # hello world

```

#### 字符串比较

对于两个字符串类型的变量，可以直接使用比较运算符比较两个字符串的相等性或大小。因为字符串在计算机内存中也是以二进制形式存在的，那么字符串的大小比较比的是每个字符对应的编码的大小。例如A的编码是65，需要说 而a的编码是97

#### 判断一个字符串中是否存在另外一个字符

Python 中可以用in和not in判断一个字符串中是否存在另外一个字符或字符串，in和not in运算通常称为成员运算，会产生布尔值True或False。

```scheme

s1 = 'hello, world'
print('wo' in s1)    # True
s2 = 'goodbye'
print(s2 in s1)      # False

```

#### 获取字符串长度
使用内置函数len()


### 字符串索引

正向索引:运算符是[n]，其中n是一个整数，假设字符串的长度为N，那么n可以是从0到N-1的整数，其中0是字符串中第一个字符的索引，而N-1是字符串中最后一个字符的索引.

负向索引:字符串的索引也可以是从-1到-N的整数，其中-1是最后一个字符的索引，而-N则是第一个字符的索引.

```scheme

s = 'abc123456'
N = len(s)

# 获取第一个字符
print(s[0], s[-N])    # a a

# 获取最后一个字符
print(s[N-1], s[-1])  # 6 6

# 获取索引为2或-7的字符
print(s[2], s[-7])    # c c

# 获取索引为5和-4的字符
print(s[5], s[-4])    # 3 3

```

### 字符串切片

运算符是[i:j:k]
其中i是开始索引，索引对应的字符可以取到；
j是结束索引，索引对应的字符不能取到；
k是步长，默认值为1，表示从前向后获取相邻字符的连续切片，所以:k部分可以省略。

```scheme

s = 'abc123456'

# i=2, j=5, k=1的正向切片操作
print(s[2:5])       # c12

# i=2, j=9, k=1的正向切片操作
print(s[2:])        # c123456

# i=0, j=9, k=2的正向切片
print(s[::2])       # ac246

# i=-1, j=-10, k=-1的负向切片
print(s[::-1])      # 654321cba

# i=-1, j=-10, k=-2的负向切片
print(s[::-2])      # 642ca

```

###字符串的分割
将字符串按照一定的规则分割成一个列表。

```scheme

s = 'apple,banana,cherry'
lst = s.split(',')
print(lst)  # 输出 ['apple', 'banana', 'cherry']

```

### 字符串的替换

```scheme

s = 'Hello, world!'
new_str = s.replace('world', 'Python')
print(new_str)  # Hello, Python!

```

### 字符串大小写转换

```scheme

s = 'Hello World'
upper_str = s.upper()
print(upper_str)  # 输出 HELLO WORLD

lower_str = upper_str.lower()
print(lower_str)  # 输出 hello world

```

### 判断某个字符是否是数字，字母或空格

 Python 中可以使用内置函数isnumeric、isalpha和isspace来判断。

```scheme

num_str = '123456'
alpha_str = 'abc'
space_str = ' '

# 使用内置函数 isnumeric 判断字符串是否只包含数字
print(num_str.isnumeric()) # True
print(alpha_str.isnumeric()) # False
print(space_str.isnumeric()) # False

# 使用内置函数 isalpha 判断字符串是否只包含字母
print(num_str.isalpha()) # False
print(alpha_str.isalpha()) # True
print(space_str.isalpha()) # False

# 特别地，在 Python 中，中文也是字母
cn_alpha_str = '你好'
print(cn_alpha_str.isalpha()) # True (中文也是字母)

# 使用内置函数 isspace 判断字符串是否只包含空格
print(space_str.isspace()) # True
print(num_str.isspace()) # False
print(alpha_str.isspace()) # False

```