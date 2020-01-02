# Python

* [什么是 Python 生成器？](#什么是-Python-生成器)
* [什么是 Python 迭代器？](#什么是-Python-迭代器)
* [list 和 tuple 有什么区别？](#list-和-tuple-有什么区别)
* [Python 中的 list 和 dict 是怎么实现的？](#Python-中的-list-和-dict-是怎么实现的)
* [Python 中使用多线程可以达到多核CPU一起使用吗？](#Python-中使用多线程可以达到多核CPU一起使用吗)
* [什么是装饰器？](#什么是装饰器)
* [Python 如何进行内存管理？](#Python-如何进行内存管理)
* [Python 中的垃圾回收机制？](#Python-中的垃圾回收机制)
* [什么是 lambda 表达式？](#什么是-lambda-表达式)
* [什么是深拷贝和浅拷贝？](#什么是深拷贝和浅拷贝)
* [双等于和 is 有什么区别？](#双等于和-is-有什么区别)
* [其它 Python 知识点](#其它-Python-知识点)
* [参考](#参考)

------

## 什么是 Python 生成器？
generator，有两种产生生成器对象的方式：一种是列表生成式加括号：

```g1 = (x for x in range(10))```

一种是在函数定义中包含```yield```关键字：

```py
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'

g2 = fib(8)
```

对于generator对象g1和g2，可以通过```next(g1)```不断获得下一个元素的值，如果没有更多的元素，就会报错```StopIteration```

也可以通过for循环获得元素的值。

生成器的好处是不用占用很多内存，只需要在用的时候计算元素的值就行了。

## 什么是 Python 迭代器？
Python中可以用于for循环的，叫做可迭代```Iterable```，包括list/set/tuple/str/dict等数据结构以及生成器；可以用以下语句判断一个对象是否是可迭代的：

```py
from collections import Iterable
isinstance(x, Iterable)
```

迭代器```Iterator```，是指可以被```next()```函数调用并不断返回下一个值，直到```StopIteration```；生成器都是Iterator，而列表等数据结构不是；可以通过以下语句将list变为Iterator：

```iter([1,2,3,4,5])```

生成器都是Iterator，但迭代器不一定是生成器。

## list 和 tuple 有什么区别？
- list 长度可变，tuple不可变；
- list 中元素的值可以改变，tuple 不能改变；
- list 支持```append```; ```insert```; ```remove```; ```pop```等方法，tuple 都不支持

## Python 中的 list 和 dict 是怎么实现的？

## Python 中使用多线程可以达到多核CPU一起使用吗？

Python中有一个被称为Global Interpreter Lock（GIL）的东西，它会确保任何时候你的多个线程中，只有一个被执行。线程的执行速度非常之快，会让你误以为线程是并行执行的，但是实际上都是轮流执行。经过GIL这一道关卡处理，会增加执行的开销。

可以通过多进程实现多核任务。

## 什么是装饰器？

## Python 中的垃圾回收机制？
[Python垃圾回收机制--完美讲解!](https://www.jianshu.com/p/1e375fb40506)

## 什么是 lambda 表达式？
简单来说，lambda表达式通常是当你需要使用一个函数，但是又不想费脑袋去命名一个函数的时候使用，也就是通常所说的匿名函数。

lambda表达式一般的形式是：关键词lambda后面紧接一个或多个参数，紧接一个冒号“：”，紧接一个表达式

## 什么是深拷贝和浅拷贝？
赋值（=），就是创建了对象的一个新的引用，修改其中任意一个变量都会影响到另一个。

浅拷贝 copy.copy：创建一个新的对象，但它包含的是对原始对象中包含项的引用（如果用引用的方式修改其中一个对象，另外一个也会修改改变）

深拷贝：创建一个新的对象，并且递归的复制它所包含的对象（修改其中一个，另外一个不会改变）{copy模块的deep.deepcopy()函数}

## 双等于和 is 有什么区别？
```==```比较的是两个变量的 value，只要值相等就会返回True

```is```比较的是两个变量的 id，即```id(a) == id(b)```，只有两个变量指向同一个对象的时候，才会返回True

但是需要注意的是，比如以下代码：

```
a = 2
b = 2
print(a is b)
```

按照上面的解释，应该会输出False，但是事实上会输出True，这是因为Python中对小数据有缓存机制，-5~256之间的数据都会被缓存。

------

## 其它 Python 知识点

### 类型转换
- list(x)
- str(x)
- set(x)
- int(x)
- tuple(x)

### try...except

### list
- ```lst[a:b]```：左闭右开
- ```lst.append(value)```：在末尾添加元素，复杂度O(1)
- ```lst.pop()```：弹出列表末尾元素，复杂度O(1)
- ```lst.pop(index)```：弹出任意位置元素，将后面的元素前移，复杂度O(n)
- ```lst.insert(index, value)```：插入元素，后面的元素后移，复杂度O(n)
- ```lst.remove(value)```：移除等于value的第一个元素，后面的元素前移，复杂度O(n)
- ```lst.count(value)```：计数值为value的元素个数
- ```lst.sort(reverse = False)```：排序，默认升序

### 参考
- [生成器 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/1016959663602400/1017318207388128)
- [Python中的is和==的区别](https://www.cnblogs.com/yjtxin/p/11793243.html)