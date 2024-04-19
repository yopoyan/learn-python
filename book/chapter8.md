
# 列表

Python 已经为我们内置了多种基本的数据结构，例如：列表、字典、集合、元组等，每一种数据结构都有其特定的用途和优势，可以根据不同的需求来选择使用。
列表是一种可变的数据类型。

### 定义和使用列表

在 Python 中，我们可以使用列表来描述它，列表是由一系列元素按特定顺序构成的数据序列，通常使用[]字面量语法来定义列表，列表中的多个元素用逗号进行分隔，并且元素是可以重复的，代码如下所示：

```scheme

hobbies = ['swim', 'fitness','running'] # 游泳、健身、跑步
print(hobbies)  


```

### 使用列表生成式创建列表


```scheme

# 将 1-10 的平方放入一个列表中
squares = [x ** 2 for x in range(1, 11)] # 一行代码生成一个列表，是不是很简单
print(squares) # 输出结果为 [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]


# 将 1-10 中的偶数放入一个列表中
numbers = [x for x in range(1, 11) if x % 2 == 0]
print(numbers) # 输出结果为 [2, 4, 6, 8, 10]


```

### 使用 list 构造器创建列表

通过 Python 内置的 list 函数将其他序列变成列表。准确的说，list并不是一个普通的函数，它是创建列表对象的构造器函数，它可以接受一个可迭代对象作为可选参数，例如元组、字符串、集合等

```scheme

hobbies = list() # 创建一个空列表


hello = list('hello') # 创建一个字符列表
print(hello) 
# ['h', 'e', 'l', 'l', 'o']


```

### 列表的索引

列表跟字符串一样，其中的元素可以通过索引来访问，索引是整数值，从 0 开始，表示列表中的第一个元素。

```scheme

hobbies = ['swim', 'fitness','running']
print(hobbies[0])    # 'swim'


```

### 列表的拼接

```scheme

items1 = [35, 12, 99, 68, 55, 87]
items2 = [45, 8, 29]

# 列表的拼接，可以直接使用加法运算符，会将 item2 的列表元素追加到 item1 之后
items3 = items1 + items2
print(items3)    
# [35, 12, 99, 68, 55, 87, 45, 8, 29]

```

### 列表的切片

可以使用切片来获取列表中的一部分元素。切片的语法是 my_list[start:end]，其中 start 表示切片起始位置，end 表示切片结束位置（但不包含该位置的元素）。

例如，my_list[1:3]将返回列表中的第二个和第三个元素。注意，列表切片会返回一个全新的列表，不会对原列表做出任何改变哦。

```scheme

items1 = [35, 12, 99, 68, 55, 87]

# 列表的切片
print(items1[:5])
print(items1[4:])

```

### 获取列表长度

使用 len 函数来获取长度

```scheme

# 获取列表的长度(元素个数)
items = ['Python', 'Java', 'Go', 'Kotlin']
size = len(items)
print(size)

```

### 判断某个元素是否在列表内

可以使用 in 关键字来做判断

```scheme

print('Python' in ['Python', 'Java', 'Go', 'Kotlin']) # True
print('JS' in ['Python', 'Java', 'Go', 'Kotlin']) # False

```

### 列表的方法

作为一个可变的数据容器，列表提供了丰富的方法供我们使用，例如动态添加、删除、更新、对元素排序等等。

#### 添加元素

```scheme

items = ['Python', 'Java', 'Go', 'Kotlin']
# 使用 append 方法在列表尾部添加元素
items.append('Swift')
print(items)    # ['Python', 'Java', 'Go', 'Kotlin', 'Swift']
# 使用 insert 方法在列表指定索引位置插入元素,注意索引是从 0 开始。
items.insert(2, 'SQL')
print(items)    # ['Python', 'Java', 'SQL', 'Go', 'Kotlin', 'Swift']

```

#### 删除元素

```scheme

# 删除指定内容的元素
items = ['Python', 'Java', 'Go', 'Kotlin', 'Swift']
items.remove('Java')
print(items)    # ['Python', 'SQL', 'Go', 'Kotlin', 'Swift']

# 删除列表尾部的元素，并将删除的值返回
last_element = items.pop()
print(last_element)
print(items)

# 删除指定索引位置的元素
items.pop(0)
print(items)

# 清空列表中的元素
items.clear()
print(items)    # []

```

#### 更新元素

```scheme

items = ['Python', 'Java', 'Go', 'Kotlin', 'Swift']
items[0] = 'JS' # 更新索引 0 位置上的元素
print(items)

```

#### 查找元素在列表中的索引

列表的 index 方法用于查找某个元素在列表中第一次出现的位置，
语法如下：index(element[, start[, end]])，
其中 element 是要查找的元素，start 和 end 是可选参数，用于指定查找的起始和结束位置。
如果指定了 start，那么查找将从该位置开始；
如果指定了 end，那么查找将在该位置结束（但不包括该位置）。


```scheme

items = ['Python', 'Java', 'Java', 'Go', 'Kotlin', 'Python']

# 查找元素的索引位置
print(items.index('Python'))       # 0
print(items.index('Python', 2))    # 5
print(items.index('Java', 3))

```

#### 查找元素在列表中出现的次数

列表类型的 count 方法用来统计一个元素在列表中出现的次数

```scheme

items = ['Python', 'Java', 'Java', 'Go', 'Kotlin', 'Python']

# 查找元素出现的次数
print(items.count('Python'))    
# 2

```

#### 元素排序

列表的 sort 操作可以实现列表元素的就地排序，语法如下：

```scheme

list.sort(key=None, reverse=False)


```

其中，key 和 reverse 都是可选参数。key 是一个函数，用于指定排序的关键字（默认为 None），一般用在列表的元素为符合类型，比如元素还是一个列表，或者是我们后续学的字典等等，后续我们会再次介绍；reverse 是一个布尔值，用于指定排序的顺序（默认为 False，即升序）。

```scheme
items = ['Python', 'Java', 'Go', 'Kotlin', 'Python']

# 升序排序
items.sort()
print(items)    # ['Go', 'Java', 'Kotlin', 'Python', 'Python']

# 降序排序
items.sort(reverse=True)
print(items) # ['Python', 'Python', 'Kotlin', 'Java', 'Go']

```

#### 元素反转

reverse 操作可以实现元素的反转

```scheme

items = ['Python', 'Java', 'Go', 'Kotlin', 'Python']

# 反转
items.reverse()
print(items)    # ['Python', 'Kotlin', 'Go', 'Java', 'Python']

```

#### 其他方法

```scheme

numbers = [2,4,6,8]
print(max(numbers)) # 输出列表中的最大值
print(min(numbers)) # 输出最小值
print(sum(numbers)) # 输出所有元素的和


```

### 遍历列表元素

```scheme

items = ['Python', 'Java', 'Go', 'Kotlin']

for item in items:
    print(item)

```

如果需要获取列表中每个元素所在的索引，推荐使用 enumerate 函数遍历列表获取索引：
enumerate 函数接收一个可迭代的序列，本质上返回了一个枚举对象，其中对象里每个元素都是一个元组，包含了传入元素的元素的下标和值，所以遍历的时候可以同时取出下标和值两个变量。


```scheme

items = ['Python', 'Java', 'Go', 'Kotlin']

for index, item in enumerate(items):
    print(index, item)

```


### 二维列表

二维列表是一个元素为列表的列表，也可以叫嵌套列表，它可以用来标识二维数组、数学中的矩阵等数据结构。由于 Python 语言没有限定列表中的元素必须是相同的数据类型，也就是说一个列表中的元素可以任意的数据类型，当然也包括列表。

```scheme


students = []
for i in range(0, 5):
    scores = []
    for j in range(0,3):
        scores.append(0)
    students.append(scores)

print(students) 
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]


```

#### 访问二维列表中的元素

```scheme

students = []
for i in range(0, 5):
    scores = []
    for j in range(0,3):
        scores.append(0)
    students.append(scores)
# 索引第 2 个学生的第 3 门成绩
value = students[1][2]
print(value) # 0

students[1][2] = 100
value2 = students[1][2]
print(value2) # 100

```


#### 二维列表的遍历

```scheme

my_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

for row in my_list:
    for element in row:
        print(element, end=' ') # 还记得 end 参数的作用吧
    print()

```