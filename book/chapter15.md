
# 文件的基本操作
在Python 里 文件的3种常用的操作模式

'r'	读取 （默认）
'w'	写入（会先清除之前的内容）
'a'	追加，将内容写入到已有文件的末尾

## 写文本文件


```scheme

file = open('hello.txt', 'a', encoding='utf-8')
file.write('你好，Python4。\n')
file.close()

print('文件已写入')


```

## 读文本文件

用open函数打开文本文件时，需要指定文件名并将文件的操作模式设置为'r'，如果不指定，默认值也是'r'；如果需要指定字符编码，可以传入 encoding 参数，如果不指定，默认值是 None

```scheme

# 读取文件
file = open('hello.txt', 'r', encoding='utf-8')
print(file.read())
file.close()


```

除了使用文件对象的 read 方法读取文件之外，还可以使用for-in循环逐行读取或者用readlines方法将文件按行读取到一个列表容器中，代码如下所示。

```scheme


file = open('hello.txt', 'r', encoding='utf-8')
for line in file:
    print(line)
file.close()


file = open('hello.txt', 'r', encoding='utf-8')
lines = file.readlines()
for line in lines:
    print(line)
file.close()


```

## 使用 with 语句读写文件

Python 还提供一种 with-as 语法在做到在读写完文件后自动执行 close 逻辑。

```scheme

with open('hello.txt', 'a', encoding='utf-8') as f:
    f.write('你好，Python5。\n')

```

# 对象的序列化和反序列化

介绍一下 json模块 

dump - 将 Python 对象按照 JSON 格式序列化到文件中
dumps - 将 Python 对象处理成 JSON 格式的字符串
load - 将文件中的 JSON 数据反序列化成对象
loads - 将字符串的内容反序列化成 Python 对象


## 将对象转成 JSON 字符串

```scheme

import json

my_dict = {
    'name': "xiaoming",
    'age': 20,
    'hobbies': ["running", "swim"],
    'teachers': [
        {
            'name': '张老师',
            'age': 31,
        }
    ]
}


print(json.dumps(my_dict))
print(json.dumps(my_dict, ensure_ascii=False))

```

需要注意的是，如果数据中有中文，需要在 dumps 函数中指定 ensure_ascii=False，不然输出的中文会被 unicode 字符编码代替。

## 将 JSON 字符串转成对象

```scheme

import json

my_dict_str = '{"name": "xiaoming", "age": 20, "hobbies": ["running", "swim"], "teachers": [{"name": "张老师", "age": 31}]}'
try:
    my_dict = json.loads(my_dict_str) 
    print(my_dict['name']) 
except Exception as e:
    print(e)

```

## JSON 和文件读写操作

```scheme

import json

my_dict = {
    'name': "xiaoming",
    'age': 20,
    'hobbies': ["running", "swim"],
    'teachers': [
        {
            'name': '张老师',
            'age': 31,
        }
    ]
}

# 序列化
with open('data.json', 'w') as file:
    json.dump(my_dict, file)

# 反序列化
with open('data.json', 'r') as file:
    my_dict_2 = json.load(file)
    print(type(my_dict_2))
    print(my_dict_2['name'])

```

# 用 Python 读写 CSV 文件

## CSV 文件介绍
CSV（Comma Separated Values）全称逗号分隔值文件是一种简单、通用的文件格式，被广泛的应用于应用程序（数据库、电子表格等）数据的导入和导出以及异构系统之间的数据交换。因为 CSV 是纯文本文件，不管是什么操作系统和编程语言都是可以处理纯文本的，而且很多编程语言中都提供了对读写 CSV 文件的支持，因此 CSV 格式在数据处理和数据科学中被广泛应用。

CSV 文件有以下特点：

    纯文本；
    由一条条的记录组成（典型的是每行一条记录）；
    每条记录被分隔符（如逗号、分号、制表符等）分隔为字段（列）；
    每条记录都有同样的字段序列。

CSV 文件可以使用文本编辑器或类似于 Excel 电子表格这类工具打开和编辑，当使用 Excel 这类电子表格打开 CSV 文件时，你甚至感觉不到 CSV 和 Excel 文件的区别。很多数据库系统都支持将数据导出到 CSV 文件中，当然也支持从 CSV 文件中读入数据保存到数据库中。


```scheme


import csv
import random

with open('scores.csv', 'w') as file:
    writer = csv.writer(file)
    # 先写入第一行：列名
    writer.writerow(['姓名', '语文', '数学', '英语'])
    names = ['关羽', '张飞', '赵云', '马超', '黄忠']
    for name in names:
        scores = [random.randint(50, 101) for _ in range(3)]
        scores.insert(0, name)
        writer.writerow(scores)

with open('scores.csv', 'r') as file:
    print(file.read())

```

## 从 CSV 文件读取数据

```scheme

import csv
import random
with open('scores.csv', 'w') as file:
    writer = csv.writer(file)
    # 先写入第一行：列名
    writer.writerow(['姓名', '语文', '数学', '英语'])
    names = ['关羽', '张飞', '赵云', '马超', '黄忠']
    for name in names:
        scores = [random.randint(50, 101) for _ in range(3)]
        scores.insert(0, name)
        writer.writerow(scores)

with open('scores.csv', 'r') as file:
    reader = csv.reader(file)
    # data_list 是一个列表对象，该列表对象包含了一行中所有的字段。
    for data_list in reader:
        # 我们会给读到的数据打印出行信息
        print(reader.line_num, end='\t')
        for elem in data_list:
            # 打印行里面的每一个字段
            print(elem, end='\t')
        print()


```