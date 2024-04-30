
# 字典


```scheme

User1 = ['Stan', 25, 'running'] # 列表
User2 = ('Stan', 25, 'running') # 元组
User3 = {'Stan', 25, 'running'} # 集合

```

这几种数据结构最大的问题是，我们无法直观的知道每个元素代表的具体的含义，因此，我们需要一种新的数据组织方式，能够将元素的含义和具体的值组合在一起的数据结构，这便是字典。

### 创建和使用字典

```scheme

user = {
    'Name': 'Stan',
    'Age': 28,
    'hobby': 'running',
}
print(user)

```

我们也可以使用内置函数 dict 来创建字典。

```scheme

user = dict(name='Stan', age=28, hobby='running')
print(user)

Result:
{'name': 'Stan', 'age': 28, 'hobby': 'running'}


```

### 如何获取字典中有多少个键值对

```scheme

user = dict(name='Stan', age=28, hobby='running')
print(len(user)) # 3

```

### 判断某个键是否在字典中

```scheme

user = dict(name='Stan', age=28, hobby='running')
print('name' in user, 'tel' in user)    

# True False

```

### 字典的索引

```scheme

# 修改用户的年龄
user = dict(name='Stan', age=28, hobby='running')
print(user['name'])
# 因为字典是可变类型，也可以通过索引修改对应的值
if 'age' in user:
    user['age'] = 25
    print(user)

```

字典中的键必须是不可变类型，例如整数（int）、浮点数（float）、字符串（str）、元组（tuple）等类型的值；显然，列表（list）和集合（set）是不能作为字典中的键的，当然字典类型本身也不能再作为字典中的键，因为字典也是可变类型，但是字典可以作为字典中的值。

## 字典的方法

### 获取字典中某个键对应的值

可以使用字典自带的 get 方法通过键获取对应的值

```scheme

user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}

print(user.get('name'))    # 'Stan'
print(user.get('address'))    # None
print(user.get('address', 'Shanghai'))    # Shanghai

```

### 获取字典中所有的键值

```scheme

user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}

# 获取字典中所有的键
print(user.keys()) # dict_keys(['name', 'age', 'hobby'])
# 获取字典中所有的值
print(user.values()) # dict_values(['Stan', 28, 'running'])
# 获取字典中所有的键值对
print(user.items()) # dict_items([('name', 'Stan'), ('age', 28), ('hobby', 'running')])

```

### 删除字典中的某个键值对

```scheme

user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}
# 使用pop方法通过键删除对应的键值对并返回值
ageValue = user.pop('age')
print(ageValue) # 28
print(len(user)) #2

# 使用 popitem 方法删除字典中最后一组键值对并返回对应的二元组（这便是元组的一个应用，作为函数返回值）
# 如果字典中没有元素，调用该方法将引发KeyError异常
key, value = user.popitem()
print(key, value) # hobby running

```

### 向字典中插入键值对

```scheme

user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}

# 通过索引直接插入
user['address'] = 'Shanghai'



user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}
# 如果这个键在字典中存在，setdefault 返回原来与这个键对应的值
# 如果这个键在字典中不存在，向字典中添加键值对，返回第二个参数的值，默认为 None
result = user.setdefault('address', 'Shanghai')
print(result) # Shanghai
print(user) 

# {'name': 'Stan', 'age': 28, 'hobby': 'running', 'address': 'Shanghai'}

```

### 向字典中更新键值对

```scheme

user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}

# 通过索引直接插入
user['age'] = 25
print(user)

# 注意，update 方法传入的也是一个字典，相当于将参数合并到原字典中
user.update({'address': 'Shanghai'})
user.update({'age': 25})
print(user)


```

### 从字典中删除键值对

```scheme

user = {'name': 'Stan', 'age': 28, 'hobby': 'running'}
del user['age']
print(user)

```

## 遍历字典

### 遍历字典中的键


```scheme

user = {'Name': 'Stan', 'Age': 28, 'hobby': 'running'}
for key in user:
    print(key)

```

### 遍历字典中的值

```scheme

user = {'Name': 'Stan', 'Age': 28, 'hobby': 'running'}

for value in user.values():
    print(value)

```

### 遍历字典中的键和值

```scheme

user = {'Name': 'Stan', 'Age': 28, 'hobby': 'running'}

for key, value in user.items():
    print(key, value)

```