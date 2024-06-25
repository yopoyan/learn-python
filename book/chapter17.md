
# 迭代器和可迭代对象

## 迭代器

对象本质上是一个类的实例，而在一个类中我们可以定义其对应的方法。迭代器本质上也是一个对象，是一个实现了 __iter__() 和 __next__() 方法的对象。

它用于遍历可迭代对象中的元素。其中，__iter__() 方法会返回它自身，__next__() 方法用于返回本次迭代应该返回的元素，直到没有元素可返回时，需要抛出 StopIteration 异常。


```scheme

# 创建一个自定义迭代器
# 实现了 __iter__ 方法，实际上就是返回自身
# 实现了 __next__ 方法，定义了该如何去获取下一个元素
class MyIterator:
    def __init__(self, data):
        self.data = data
        self.index = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.index >= len(self.data):
            # 需要停止迭代时需要抛出异常
            raise StopIteration
        item = self.data[self.index]
        self.index += 1
        return item

# 传入参数，创建一个自定义迭代器
my_iterator = MyIterator([1, 2, 3, 4, 5])

# 使用循环遍历可迭代对象中的元素
for item in my_iterator:
    print(item)

```


## 可迭代对象


可迭代对象是指实现了 __iter__() 方法的对象，它可以被迭代。该方法实际上会返回一个迭代器，就是我们上面所说的那个。

```scheme
class MyIterable:
    def __init__(self, data):
        self.data = data

    def __iter__(self):
        # 返回一个迭代器对象
        return MyIterator(self.data)

class MyIterator:
    def __init__(self, data):
        self.data = data
        self.index = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.index >= len(self.data):
            raise StopIteration
        item = self.data[self.index]
        self.index += 1
        return item

# 创建一个可迭代对象
my_iterable = MyIterable([1, 2, 3, 4, 5])

# 使用循环遍历可迭代对象中的元素
for item in my_iterable:
    print(item)

```


## yield 关键字和生成器

Python 中，生成器（Generator）是一种特殊的迭代器，它可以通过函数来创建。生成器函数使用 yield 关键字来产生一个值，并且在每次调用 yield 时暂停执行，保留函数的状态，以便下次调用时可以从上次暂停的地方继续执行。


生成器具有以下特点：

1、生成器函数使用 def 关键字定义，但是它们的执行方式与普通函数不同。当生成器函数被调用时，它返回一个生成器对象，而不是立即执行函数体。
2、生成器对象是可迭代的，可以在循环中使用，并且可以通过调用 next() 函数来获取下一个值。每次调用 next() 函数时，生成器函数会从上次暂停的地方继续执行，直到遇到下一个 yield 语句。
3、生成器函数可以使用 yield 语句产生一个值，并将该值返回给调用者。生成器函数可以多次使用 yield 语句来产生多个值。


```scheme

def my_generator():
    yield 1
    yield 2
    yield 3
    yield 4
    yield 5

# 创建一个生成器对象
my_generator_obj = my_generator()

# 使用循环遍历生成器中的值
for item in my_generator_obj:
    print(item)
    

```

## 函数的闭包

闭包是指在一个函数内部定义的函数，并且该内部函数可以访问外部函数的变量。

```scheme

def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure = outer_function(10)
print(closure(5))  # 输出 15

```

在上面的例子中，outer_function 是外部函数，它接受一个参数 x。在外部函数内部，定义了一个内部函数 inner_function，它接受一个参数 y。 内部函数 inner_function 访问了外部函数的变量 x，并将 x 和 y 相加返回。 当调用 outer_function(10) 时，它返回了内部函数 inner_function 的引用，并且 x 的值被保存在闭包中。我们将这个闭包赋值给变量 closure。 然后，我们可以通过调用 closure(5) 来使用闭包，它会将 5 作为参数传递给内部函数 inner_function，并返回 15。

## 闭包好处

1、可以在函数内部创建一个私有的作用域，保护变量不被外部访问和修改。
2、闭包还可以延长变量的生命周期，使得变量在函数执行完毕后仍然可以被访问和使用。

```scheme

def counter():
    count = 0
    def increment():
        nonlocal count
        count += 1
        return count

    return increment

# 创建两个计数器
counter1 = counter()
counter2 = counter()

print(counter1())  # 输出 1
print(counter1())  # 输出 2
print(counter2())  # 输出 1
print(counter2())  # 输出 2

```

## global 与 nonlocal


global 和 nonlocal 是 Python 中的两个关键字，它们可以用来修改变量的作用域。 global 用来声明一个变量的作用域为全局作用域，即在函数内部修改变量的值时，Python 会认为我们在修改全局变量的值，而不是定义一个新的局部变量。 对于上面的例子，我们可以使用 global 关键字来修改变量 x 的作用域：


```scheme

x = 10
def func():
    global x # 声明x为全局变量
    x = 20
    print("in func: x = ", x) # 尝试在函数func中输出x的值
func()
print("out func: x = ", x) # 尝试在函数func外输出x的值


```

对于闭包函数，我们可以使用 nonlocal 关键字来修改变量的作用域：

```scheme

x = 10
def func():
    x = 20
    def inner_func():
        nonlocal x # 声明x为嵌套变量
        x = 30
        print("in inner_func: x = ", x) # 尝试在函数闭包中输出x的值
    inner_func()
    print("in func: x = ", x) # 尝试在函数func中输出x的值
func()
print("out func: x = ", x) # 尝试在函数func外输出x的值

```

在上面的代码中，我们希望在函数 inner_func 中修改变量 x 的值，但是如果直接修改变量 x 的值，Python 会认为我们在函数 inner_func 中定义了一个新的局部变量 x，而不是修改函数 func 中的变量 x。 而如果使用了 global 关键字，Python 会认为我们在修改全局变量 x 的值，而不是修改 func 中的变量 x。 这就需要使用 nonlocal 关键字来声明变量 x 为嵌套变量，即在函数 func 中定义的变量 x，而不是全局变量 x。

