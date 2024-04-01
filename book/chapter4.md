
# Python 运算符

Python 支持多种运算符，按照运算符的优先级从上到下列出了各种运算符。
所谓优先级就是在一个运算的表达式中，如果搞不清楚运算符的优先级，可以使用圆括号来确保运算的执行顺序。

- [] [:] 下标，切片
- ** 指数
- ~ + - 按位取反, 正负号
- * / % //  乘，除，模（余数），整除
- + - 加，减
- >> << 右移，左移
- & 按位与
- ^ | 按位异或，按位或
- <= < > >=  小于等于，小于，大于，大于等于
- == != 等于，不等于
- is is not 身份运算符
- in not in 成员运算符
- not or and 逻辑运算符
- = += -= *= /= %= //= **= &= |= ^= >>= <<=  （复合）赋值运算符

### 算术运算符

```scheme

print(1 + 1)     # 加法运算
print(5 - 4)     # 减法运算
print(6 * 7)     # 乘法运算
print(14 / 2)     # 除法运算
print(58 % 25)     # 求模（余数）运算
print(85 // 3)    # 整除运算
print(79 ** 2)    # 求幂运算


```

### 赋值运算符和复合赋值运算符

```scheme

a = 10
b = 3
a += b        # 相当于：a = a + b
a *= a + 2    # 相当于：a = a * (a + 2)
print(a)      # 算一下这里会输出什么

```

### 比较运算符和逻辑运算符

比较运算符的优先级高于赋值运算符，所以flag0 = 1 == 1先做1 == 1产生布尔值True，再将这个值赋值给变量flag0。print函数可以输出多个值，多个值之间可以用,进行分隔，输出的内容之间默认以空格分开。

```scheme

"""
比较运算符和逻辑运算符的使用

"""
flag0 = 1 == 1
flag1 = 3 > 2
flag2 = 2 < 1
flag3 = flag1 and flag2
flag4 = flag1 or flag2
flag5 = not (1 != 2)
print('flag0 =', flag0)    # flag0 = True
print('flag1 =', flag1)    # flag1 = True
print('flag2 =', flag2)    # flag2 = False
print('flag3 =', flag3)    # flag3 = False
print('flag4 =', flag4)    # flag4 = True
print('flag5 =', flag5)    # flag5 = False

```

### 运算符

在使用print函数输出时，也可以对字符串内容进行格式化处理，上面print函数中的字符串%.1f是一个占位符，稍后会由一个float类型的变量值替换掉它，.1f 意思是保留一位小数。同理，如果字符串中有%d，后面可以用一个int类型的变量值替换掉它，而%s会被字符串的值替换掉。

```scheme

f = 50
c = (f - 32) / 1.8
print('%.1f华氏度 = %.1f摄氏度' % (f, c))

#输出结果

Result:
50.0华氏度 = 10.0摄氏度


```

### 例子

正确的周长和面积计算公式如下： 圆的周长公式：周长 = 2 * π * 半径 圆的面积公式：面积= π * 半径 * 半径 π = 3.1416

```scheme

radius = 3

π = 3.1416

print(2 * π *radius)

print(π * radius * radius)

```