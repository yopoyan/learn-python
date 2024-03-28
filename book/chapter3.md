

# 第三章 标准的输入和输出

### 标准输入
在 Python 中，我们使用 input() 函数来获取用户键盘输入，代码示例如下：

```scheme

name = input("请输入姓名：")
print(name)


age = input("请输入年龄：")
age = int(age)
print(type(age))
print(age)

```

### 标准输出

print() 函数来将信息输出到屏幕上

#### print 函数语法进阶

```scheme

name = "xiaoming"
age = 23
print("你好,", "我的名字是", name, ",我今年", age, "岁")

```

#### print 函数的可选参数

```scheme

name = "xiaoming"
age = 23
print(name, end=' ') # 将换行符替换成空格
print(age)
# xiaoming 23

```

####  Python 3.6+ 的 f-string 格式化方法

```scheme

# 请求用户输入他们的姓名  
name = input("请输入您的姓名: ")  
  
# 请求用户输入他们的年龄  
age = input("请输入您的年龄: ")  
  
# 使用 print 函数将姓名和年龄输出到同一行，并在结尾加上句号  
print(f"{name}的年龄是{age}岁。")

```