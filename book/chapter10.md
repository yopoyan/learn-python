
# 集合

集合的唯一性决定了集合中不能有重复元素

集合的特点：
1.无序性：集合中的元素没有顺序，不能通过下标来访问元素。
2.唯一性：集合中的元素是唯一的，不能有重复元素。
3.不可变性：集合本身是可变的，但是集合中的元素必须是不可变的，例如数字、字符串、元组等。

无序性说明集合中的元素并不像列表中的元素那样是顺序的，因为集合不可以通过索引访问。

### 创建集合

在 Python 中，创建集合可以使用{}字面量语法，{}中需要至少有一个元素，因为没有元素的{}并不是空集合而是一个空字典。


```scheme

# 创建集合的字面量语法(重复元素不会出现在集合中)
set1 = {1, 2, 3, 3, 3, 2}
print(set1)         # {1, 2, 3}


```

也可以使用内置函数 set 来创建一个集合。


```scheme

set1 = set() # 空集合
set2 = set('hello')
print(set2)         
# {'h', 'l', 'o', 'e'}

```

### 列表和集合的相互转换

```scheme

# 将列表转换成集合(可以去掉列表中的重复元素)
set3 = set([1, 2, 3, 3, 2, 1])
print(set3)         
# {1, 2, 3}


# 将集合转换成列表
list3 = list({1, 2, 3})
print(list3) 
# [1, 2, 3]

```

### 判断元素是否在集合中

可以通过运算符 in和not in 检查元素是否在集合中。

```scheme

set1 = {11, 12, 13, 14, 15}
print(10 in set1)        # False
print(15 in set1)        # True

```

### 交并差运算

```scheme

set1 = {1, 2, 3, 4, 5, 6, 7}
set2 = {2, 4, 6, 8, 10}

# 交集
# 方法一: 使用 & 运算符
print(set1 & set2)                # {2, 4, 6}
# 方法二: 使用 intersection 方法
print(set1.intersection(set2))    # {2, 4, 6}

# 并集
# 方法一: 使用 | 运算符
print(set1 | set2)         # {1, 2, 3, 4, 5, 6, 7, 8, 10}
# 方法二: 使用union方法
print(set1.union(set2))    # {1, 2, 3, 4, 5, 6, 7, 8, 10}

# 差集
# 方法一: 使用 - 运算符
print(set1 - set2)              # {1, 3, 5, 7}
# 方法二: 使用 difference 方法
print(set1.difference(set2))    # {1, 3, 5, 7}

```

### 集合的方法


#### 添加元素

```scheme

# 创建一个空集合
set1 = set()

# 通过add方法添加元素
set1.add(1)
set1.add(2)
print(set1) # {1, 2}

```

#### 添加多个元素

```scheme

# 创建一个空集合
set1 = set()

# 通过 update 方法添加元素
set1.update([1, 2])  # 添加多个元素
print(set1)  # # {1, 2}

```

#### 删除元素

```scheme

set1 = set([1, 2, 3, 4])
# 通过 discard 方法删除指定元素，如果元素不存在不会报错
set1.discard(1)
set1.discard(2)
print(set1)    # {3, 4}

# 通过remove方法删除指定元素，如果元素不存在会引发 KeyError 异常
set1.remove(3)
print(set1)    #{4}

# pop 方法可以从集合中随机删除一个元素并返回该元素
print(set1.pop())

```

#### 清空集合

```scheme

set1 = set([1, 2, 3, 4])
# clear方法可以清空整个集合
set1.clear()

print(set1)    # set()

```

#### 判断两个集合中有没有相同元素

如果要判断两个集合有没有相同的元素可以使用 isdisjoint 方法，没有相同元素返回True，否则返回False。

```scheme

set1 = {'Java', 'Python', 'Go', 'Kotlin'}
set2 = {'Kotlin', 'Swift', 'Java', 'Objective-C', 'Dart'}
set3 = {'HTML', 'CSS', 'JavaScript'}
print(set1.isdisjoint(set2))    # False
print(set1.isdisjoint(set3))    # True


```

### 遍历集合

```scheme

items = {1, 2, 3, 4, 5}

for item in items:
    print(item)

for index, value in enumerate(items):
    print(index, value)

```