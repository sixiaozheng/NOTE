# Python Cookbook

## unpack operation

-   tuple，list，str，file，iterator，generator 都可以执行 unpack operation. 分解未知或任意长度的可迭代对象
-   将序列分解为单独的变量
-   从任意长度的可迭代对象

```python
>>> a = [1,2,3,4,5,6,7]
>>> c,_,*d,e = a # * 表达式
>>> c
1
>>> d
[3, 4, 5, 6]
>>> e
7
>>> record = ('ACD', 5,12.3,(12,22,2012))
>>> name, *_, (*_,year) = record

# for 循环
for tag, *args in record:
    pass
```

## 保存最后N个元素

在迭代或是其他形式的处理过程中对最后迹象记录做一个有限的历史记录统计。

>   collections.deque
>
>   deque(maxlen=N)创建了一个固定长度的队列，当append新元素而队列已满时会自动移除最前面的记录。列表也可以通过（append，del）完成这种操作，但是deque更优雅，更快。从队列两端添加或弹出元素的复杂度都是O(1)，从列表的头部插入或移除元素时，复杂度是O(N)

![1565708354804](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565708354804.png)

当编写搜索某项记录的代码时，通常会用到含有`yield`关键字的生成器函数。

## 找到max N or min N元素

![1565709111136](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565709111136.png)

![1565709124090](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565709124090.png)

如果相比于集合中的元素M，N很小，可以使用堆数据结构，复杂度O(logN)

![1565709423604](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565709423604.png)

![1565709438468](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565709438468.png)

集合中的元素数M, 要找的元素数N

M很大，N很小，使用堆数据结构

N较小时，使用nlargest() , nsmallest()

N=1时，使用min(), max()

N接近M时，min: sorted(items)[:N], max: sorted(items)[-N:]

## 一键多值字典[multidict]

![1565710648233](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565710648233.png)

![1565710665068](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565710665068.png)

![1565710684179](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565710684179.png)

## 有序字典

![1565710788461](D:\research\NOTE\Mathematics\1565710788461.png)

如果进行JSON编码时精确控制各字段的顺序，只要首先在OrderedDict中构建数据就可以。

![1565710882535](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565710882535.png)

**NOTE**: OrderedDict内部维护了一个双向链表，所以大小是普通字典的2倍多，在数据比较大时，需要做好权衡。

## 与字典有关的计算

通常会利用zip()将字典的键和值反转过来，先对valus进行比较后，再对keys进行比较。

![1565762825366](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565762825366.png)

![1565762840597](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565762840597.png)

zip()创建了一个迭代器，只能使用一次

![1565763231791](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565763231791.png)

## 在两个字典中寻找相同点

在两个字典中，找出它们中间可能相同的地方（相同的键，相同的值）

![1565764202592](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565764202592.png)

修改或过滤字典

![1565764474584](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565764474584.png)

字典的keys(), items() 支持常见的集合操作，比如求并集、交集和差集。values()不支持常见的集合操作，因为不是所有的值都是唯一的，所以应该先将值转化为集合来实现。

## 从序列中移除重复项且保持元素间顺序不变

hashable：在生存期内必须是不可变的，需要有一个`__hash__()`方法，int，float，str，tuple都是不可变的。

unhashable：在生存期内必须是可变的，list，dict

![1565766563819](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565766563819.png) 

![1565766575897](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565766575897.png)

去除文件中重复的文本行：

![1565766696885](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565766696885.png)

可以通过set()去除重复项，但是不能保持元素间的顺序不变。

## 对切片命名

>   slice()

![1565767044994](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565767044994.png)

由于避免了使用许多神秘难懂的硬编码索引，代码变得更清晰

indices(size)方法将切片映射到特定大小的序列上，返回(start,stop,step)元组，所有的值都已经恰当地限制在边界以内。

![1565768121221](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565768121221.png)

## 找出序列中出现次数最多的元素

>   collections.Counter

![1565768268936](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565768268936.png)

![1565770644671](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565770644671.png)

![1565770653385](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565770653385.png)

## 通过公共键对字典列表排序

>   operator.itemgetter

![1565770829645](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565770829645.png)

![1565770840303](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565770840303.png)

![1565770850325](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565770850325.png)

![1565771438363](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565771438363.png)

![1565771448591](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565771448591.png)

## 对不原生支持比较操作的对象排序

>   operator.attrgetter()

![1565771797834](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565771797834.png)

## 根据字段将记录分组

>   itertools.groupby()

![1565772419816](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565772419816.png)

## 筛选序列中的元素

一般使用列表解析式。

缺点：原始输入非常大时，可能会产生一个庞大的结果。

解决方法：使用生成器表达式通过迭代的方式产生筛选的结果

![1565777044411](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565777044411.png)

![1565777063182](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565777063182.png)

有时候筛选的标准没法简单地表示在列表推导式或生成器表达式中，可以使用`filter()`函数

![1565777223404](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565777223404.png)

列表解析式和生成器解析式通常是用来筛选数据地最简单和最直接的方式。也可以对数据做转换的能力。

关于筛选数据，有一种情况是用新值替换掉不满足标准的值，而不是丢弃它们。可以通过将筛选条件移到一个条件表达式中来轻松实现。

![1565778151525](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565778151525.png)

>   itertools.compress

![1565778425626](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565778425626.png)

![1565778434460](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565778434460.png)

## 从字典中提取子集

字典解析式

![1565778616326](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565778616326.png)

也可以通过元组解析式，再传给dict()函数，但是字典解析式更快

![1565778808210](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565778808210.png)

## 将名称映射到序列的元素中

>   collections.namedtuple()

![1565779148448](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565779148448.png)

命名元组主要作用在于将代码同它所控制的元素位置间解耦。不需要通过位置访问数据，可以通过名称访问元素。

![1565779405958](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565779405958.png)

namedtuple是字典的替代，后者需要更多的空间来存储。因此如果要构建涉及字典的大型数据结构，使用namedtuple会更高效。但是字典可变，namedtuple不可变。

## 同时对数据做转换和换算

在函数参数中使用生成器表达式。

![1565780402850](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565780402850.png)

![1565780426877](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565780426877.png)

不必重复使用括号，以下两行代码同一个意思：

![1565780572604](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565780572604.png)

比起首先创建一个临时的列表，使用生成器做参数通常是更为高效和优雅的方式。

## 将多个映射合并为单个映射

>   collections.ChainMap

![1565781835374](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565781835374.png)

![1565781861927](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565781861927.png)

![1565781869636](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565781869636.png)

![1565781969404](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565781969404.png)

![1565781984126](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1565781984126.png)

