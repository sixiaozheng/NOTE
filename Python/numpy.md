# Numpy

## The Basics

```python
>>> import numpy as np
>>> a = np.arange(15).reshape(3, 5)
>>> a
array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14]])
>>> a.shape
(3, 5)
>>> a.ndim
2
>>> a.dtype.name
'int64'
>>> a.itemsize
8
>>> a.size
15
>>> type(a)
<type 'numpy.ndarray'>
```

## Array Creation

```python
>>> import numpy as np
>>> a=np.array([1,2,3]) # list or tuple
>>> a
array([1, 2, 3])
>>> b=np.array((1,2,3)) # list or tuple
>>> b
array([1, 2, 3])
>>> b.dtype
dtype('int64')
>>> c=np.array([1.0,2.2,3.3])
>>> c
array([1. , 2.2, 3.3])
>>> c.dtype
dtype('float64')
```

The type of the array can also be explicitly specified at creation time:

```python
>>> c = np.array( [ [1,2], [3,4] ], dtype=complex )
>>> c
array([[ 1.+0.j,  2.+0.j],
       [ 3.+0.j,  4.+0.j]])
```

```python
>>> a=np.ones((3,3))
>>> a
array([[1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.]])
>>> a.dtype
dtype('float64') # default dtype is float64
>>> b=np.zeros((3,3),dtype=np.int16)
>>> b
array([[0, 0, 0],
       [0, 0, 0],
       [0, 0, 0]], dtype=int16)
>>> c=np.empty((2,2))
>>> c
array([[4.64857845e-310, 3.18299369e-313],
       [4.64857828e-310, 6.92025267e-310]])

# np.zeros_like(), np.ones_like(), np.empty_like()
>>> d=np.zeros_like(c)
>>> d
array([[0., 0.],
       [0., 0.]])
>>> d.dtype
dtype('float64')
>>> e=np.zeros_like(b)
>>> e
array([[0, 0, 0],
       [0, 0, 0],
       [0, 0, 0]], dtype=int16)

# random
>>> np.random.rand(3,2) # uniform distribution over [0, 1).
array([[ 0.14022471,  0.96360618],  
       [ 0.37601032,  0.25528411],  
       [ 0.49313049,  0.94909878]]) 
>>> np.random.randn(2,2) # “standard normal” distribution.
array([[ 1.08094269, -0.73779719],
       [-0.63181271,  0.96959644]])

# Construct an array by executing a function over each coordinate.The resulting array therefore has a value fn(x, y, z) at coordinate (x, y, z).
>>> np.fromfunction(lambda i, j: i == j, (3, 3), dtype=int)
array([[ True, False, False],
       [False,  True, False],
       [False, False,  True]])
>>> np.fromfunction(lambda i, j: i + j, (3, 3), dtype=int)
array([[0, 1, 2],
       [1, 2, 3],
       [2, 3, 4]])
```

```python
>>> np.arange( 10, 30, 5 )
array([10, 15, 20, 25])
>>> np.arange( 0, 2, 0.3 )                 # it accepts float arguments
array([ 0. ,  0.3,  0.6,  0.9,  1.2,  1.5,  1.8])
```

```python
>>> from numpy import pi
>>> np.linspace( 0, 2, 9 )                 # 9 numbers from 0 to 2
array([ 0.  ,  0.25,  0.5 ,  0.75,  1.  ,  1.25,  1.5 ,  1.75,  2.  ])
>>> x = np.linspace( 0, 2*pi, 100 )        # useful to evaluate function at lots of points
>>> f = np.sin(x)
```

## Printing Arrays

```Python
>>> print(np.arange(10000))
[   0    1    2 ..., 9997 9998 9999]
>>>
>>> print(np.arange(10000).reshape(100,100))
[[   0    1    2 ...,   97   98   99]
 [ 100  101  102 ...,  197  198  199]
 [ 200  201  202 ...,  297  298  299]
 ...,
 [9700 9701 9702 ..., 9797 9798 9799]
 [9800 9801 9802 ..., 9897 9898 9899]
 [9900 9901 9902 ..., 9997 9998 9999]]
>>> np.set_printoptions(threshold=np.inf) # 设置打印是不省略，也可以设置为每行显示多少个元素
>>> np.set_printoptions(threshold=6)
>>> np.arange(10000).reshape(100,100)
array([[   0,    1,    2, ...,   97,   98,   99],
       [ 100,  101,  102, ...,  197,  198,  199],
       [ 200,  201,  202, ...,  297,  298,  299],
       ...,
       [9700, 9701, 9702, ..., 9797, 9798, 9799],
       [9800, 9801, 9802, ..., 9897, 9898, 9899],
       [9900, 9901, 9902, ..., 9997, 9998, 9999]])
```

## Basic Operations

**Note**: element-wise, return **new array** 

```python
>>> a = np.array( [20,30,40,50] )
>>> b = np.arange( 4 )
>>> b
array([0, 1, 2, 3])
>>> c = a-b
>>> c
array([20, 29, 38, 47])
>>> b**2
array([0, 1, 4, 9])
>>> 10*np.sin(a)
array([ 9.12945251, -9.88031624,  7.4511316 , -2.62374854])
>>> a<35
array([ True, True, False, False])
```

```python
>>> A = np.array( [[1,1],
...             [0,1]] )
>>> B = np.array( [[2,0],
...             [3,4]] )
>>> A * B                       # elementwise product
array([[2, 0],
       [0, 4]])
>>> A @ B                       # matrix product (in python >=3.5)
array([[5, 4],
       [3, 4]])
>>> A.dot(B)                    # another matrix product
array([[5, 4],
       [3, 4]])
```

Some operations, such as `+=` and `*=`, act **in place** to modify an existing array rather than create a new one.

```python
>>> a = np.ones((2,3), dtype=int)
>>> b = np.random.random((2,3))
>>> a *= 3
>>> a
array([[3, 3, 3],
       [3, 3, 3]])
>>> b += a
>>> b
array([[ 3.417022  ,  3.72032449,  3.00011437],
       [ 3.30233257,  3.14675589,  3.09233859]])
```

当进行operation时，arrays的dtype不同时，结果转换为更一般或精确的dtype，即**向上自动转换**

许多一元运算，如求和，是`ndarray`class 的方法，所以调用形式为：`a.sum()`, `a.min()`, `a.max()` 

```python
>>> a=np.arange(10)
>>> a
array([0, 1, 2, ..., 7, 8, 9])
>>> a.sum()
45
>>> a.max()
9
>>> a.min()
0
>>> type(a.sum())
<class 'numpy.int64'>
```

默认情况下，这些操作适用于数组，就像它是一个数字列表一样，无论其形状如何。但是，通过指定`axis`参数，您可以沿数组的指定轴应用操作：

```python
>>> b = np.arange(12).reshape(3,4)
>>> b
array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])
>>>
>>> b.sum(axis=0)                            # sum of each column
array([12, 15, 18, 21])
>>>
>>> b.min(axis=1)                            # min of each row
array([0, 4, 8])
>>>
>>> b.cumsum(axis=1)                         # cumulative sum along each row
array([[ 0,  1,  3,  6],
       [ 4,  9, 15, 22],
       [ 8, 17, 27, 38]])
```

## Universal Functions 通用函数

elementwise, producing an array as output.

```python
>>> B = np.arange(3)
>>> B
array([0, 1, 2])
>>> np.exp(B)
array([ 1.        ,  2.71828183,  7.3890561 ])
>>> np.sqrt(B)
array([ 0.        ,  1.        ,  1.41421356])
>>> C = np.array([2., -1., 4.])
>>> np.add(B, C)
array([ 2.,  0.,  6.])
```

>   **See also**
>
>   [`all`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.all.html#numpy.all), [`any`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.any.html#numpy.any), [`apply_along_axis`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.apply_along_axis.html#numpy.apply_along_axis), [`argmax`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argmax.html#numpy.argmax), [`argmin`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argmin.html#numpy.argmin), [`argsort`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argsort.html#numpy.argsort), [`average`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.average.html#numpy.average), [`bincount`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.bincount.html#numpy.bincount), [`ceil`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ceil.html#numpy.ceil), [`clip`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.clip.html#numpy.clip), [`conj`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.conj.html#numpy.conj), [`corrcoef`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.corrcoef.html#numpy.corrcoef), [`cov`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cov.html#numpy.cov), [`cross`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cross.html#numpy.cross),[`cumprod`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumprod.html#numpy.cumprod), [`cumsum`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumsum.html#numpy.cumsum), [`diff`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.diff.html#numpy.diff), [`dot`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.dot.html#numpy.dot), [`floor`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.floor.html#numpy.floor), [`inner`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.inner.html#numpy.inner), *inv*, [`lexsort`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.lexsort.html#numpy.lexsort), [`max`](https://docs.python.org/dev/library/functions.html#max), [`maximum`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.maximum.html#numpy.maximum), [`mean`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mean.html#numpy.mean), [`median`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.median.html#numpy.median), [`min`](https://docs.python.org/dev/library/functions.html#min), [`minimum`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.minimum.html#numpy.minimum),[`nonzero`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nonzero.html#numpy.nonzero), [`outer`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.outer.html#numpy.outer), [`prod`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.prod.html#numpy.prod), [`re`](https://docs.python.org/dev/library/re.html#module-re), [`round`](https://docs.python.org/dev/library/functions.html#round), [`sort`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sort.html#numpy.sort), [`std`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.std.html#numpy.std), [`sum`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sum.html#numpy.sum), [`trace`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.trace.html#numpy.trace), [`transpose`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.transpose.html#numpy.transpose), [`var`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.var.html#numpy.var), [`vdot`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vdot.html#numpy.vdot), [`vectorize`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vectorize.html#numpy.vectorize), [`where`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.where.html#numpy.where)

## Indexing, Slicing and Iterating

**One-dimensional** 

```python
>>> a = np.arange(10)**3
>>> a
array([  0,   1,   8,  27,  64, 125, 216, 343, 512, 729])
>>> a[2]
8
>>> a[2:5]
array([ 8, 27, 64])
>>> a[:6:2] = -1000    # equivalent to a[0:6:2] = -1000; from start to position 6, exclusive, set every 2nd element to -1000
>>> a
array([-1000,     1, -1000,    27, -1000,   125,   216,   343,   512,   729])
>>> a[ : :-1]                                 # reversed a
array([  729,   512,   343,   216,   125, -1000,    27, -1000,     1, -1000])
>>> for i in a:
...     print(i**(1/3.))
```

**Multidimensional**

```python
>>> def f(x,y):
...     return 10*x+y
...
>>> b = np.fromfunction(f,(5,4),dtype=int)
>>> b
array([[ 0,  1,  2,  3],
       [10, 11, 12, 13],
       [20, 21, 22, 23],
       [30, 31, 32, 33],
       [40, 41, 42, 43]])
>>> b[2,3]
23
>>> b[0:5, 1]                       # each row in the second column of b
array([ 1, 11, 21, 31, 41])
>>> b[ : ,1]                        # equivalent to the previous example
array([ 1, 11, 21, 31, 41])
>>> b[1:3, : ]                      # each column in the second and third row of b
array([[10, 11, 12, 13],
       [20, 21, 22, 23]])
```

-   `x[1,2,...]` is equivalent to `x[1,2,:,:,:]`,
-   `x[...,3]` to `x[:,:,:,:,3]` and
-   `x[4,...,5,:]` to `x[4,:,:,5,:]`.

```python
>>> c = np.array( [[[  0,  1,  2],               # a 3D array (two stacked 2D arrays)
...                 [ 10, 12, 13]],
...                [[100,101,102],
...                 [110,112,113]]])
>>> c.shape
(2, 2, 3)
>>> c[1,...]                                   # same as c[1,:,:] or c[1]
array([[100, 101, 102],
       [110, 112, 113]])
>>> c[...,2]                                   # same as c[:,:,2]
array([[  2,  13],
       [102, 113]])
```

```python
>>> for row in b:
...     print(row)
...
[0 1 2 3]
[10 11 12 13]
[20 21 22 23]
[30 31 32 33]
[40 41 42 43]

>>> for element in b.flat:
...     print(element)
...
0
1
2
3
10
11
12
13
20
21
22
23
30
31
32
33
40
41
42
43
```

## Shape Manipulation

### Changing the shape of an array

Note**: return a new array

```python
>>> a.ravel()  # returns the array, flattened
array([ 2.,  8.,  0.,  6.,  4.,  5.,  1.,  1.,  8.,  9.,  3.,  6.])
>>> a.reshape(6,2)  # returns the array with a modified shape
array([[ 2.,  8.],
       [ 0.,  6.],
       [ 4.,  5.],
       [ 1.,  1.],
       [ 8.,  9.],
       [ 3.,  6.]])
>>> a.T  # returns the array, transposed
array([[ 2.,  4.,  8.],
       [ 8.,  5.,  9.],
       [ 0.,  1.,  3.],
       [ 6.,  1.,  6.]])
>>> a.T.shape
(4, 3)
>>> a.shape
(3, 4)
```

`reshape`与`resize`的区别

`reshape` return a new array, 可以使用`-1` ，`resize` modifies the array itself, 不能使用`-1`

```python
>>> a
array([0, 1, 2, ..., 7, 8, 9])
>>> a.reshape(2,-1)
array([[0, 1, 2, 3, 4],
       [5, 6, 7, 8, 9]])
>>> a
array([0, 1, 2, ..., 7, 8, 9])
>>> a.resize(2,-1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: negative dimensions not allowed
>>> a.resize(2,5)
>>> a
array([[0, 1, 2, 3, 4],
       [5, 6, 7, 8, 9]])
```

### Stacking together different arrays

`np.hstack()`  `np.column_stack`  `np.c_`

`np.vstack()`  `np.row_stack`  `np.r_`

`np.concatenate()`

```python
>>> np.vstack((a,b))
array([[ 8.,  8.],
       [ 0.,  0.],
       [ 1.,  8.],
       [ 0.,  4.]])
>>> np.hstack((a,b))
array([[ 8.,  8.,  1.,  8.],
       [ 0.,  0.,  0.,  4.]])

>>> from numpy import newaxis
>>> np.column_stack((a,b))     # with 2D arrays
array([[ 8.,  8.,  1.,  8.],
       [ 0.,  0.,  0.,  4.]])
>>> a = np.array([4.,2.])
>>> b = np.array([3.,8.])
>>> np.column_stack((a,b))     # returns a 2D array
array([[ 4., 3.],
       [ 2., 8.]])
>>> np.hstack((a,b))           # the result is different
array([ 4., 2., 3., 8.])
>>> a[:,newaxis]               # this allows to have a 2D columns vector
array([[ 4.],
       [ 2.]])
>>> np.column_stack((a[:,newaxis],b[:,newaxis]))
array([[ 4.,  3.],
       [ 2.,  8.]])
>>> np.hstack((a[:,newaxis],b[:,newaxis]))   # the result is the same
array([[ 4.,  3.],
       [ 2.,  8.]])

>>> np.concatenate((a,b),axis=0)
array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [11, 12, 13, 14, 15],
       [16, 17, 18, 19, 20]])
>>> np.concatenate((a,b),axis=1)
array([[ 0,  1,  2,  3,  4, 11, 12, 13, 14, 15],
       [ 5,  6,  7,  8,  9, 16, 17, 18, 19, 20]])

# 可以使用`:`
>>> np.r_[1:4,0,4]
array([1, 2, 3, 0, 4])
```

### Splitting one array into several smaller ones

`vsplit` 

`array_split` specify the axis to split

```python
>>> a
array([[ 9.,  5.,  6.,  3.,  6.,  8.,  0.,  7.,  9.,  7.,  2.,  7.],
       [ 1.,  4.,  9.,  2.,  2.,  1.,  0.,  6.,  2.,  2.,  4.,  0.]])
>>> np.hsplit(a,3)   # Split a into 3
[array([[ 9.,  5.,  6.,  3.],
       [ 1.,  4.,  9.,  2.]]), array([[ 6.,  8.,  0.,  7.],
       [ 2.,  1.,  0.,  6.]]), array([[ 9.,  7.,  2.,  7.],
       [ 2.,  2.,  4.,  0.]])]
>>> np.hsplit(a,(3,4))   # Split a after the third and the fourth column
[array([[ 9.,  5.,  6.],
       [ 1.,  4.,  9.]]), array([[ 3.],
       [ 2.]]), array([[ 6.,  8.,  0.,  7.,  9.,  7.,  2.,  7.],
       [ 2.,  1.,  0.,  6.,  2.,  2.,  4.,  0.]])]
```

## Copies and Views

易混淆的地方

### No Copy at All

Simple assignments make no copy of array objects or of their data.

```python
>>> a = np.arange(12)
>>> b = a            # no new object is created
>>> b is a           # a and b are two names for the same ndarray object
True
>>> b.shape = 3,4    # changes the shape of a
>>> a.shape
(3, 4)
```

Python将可变对象作为引用传递，因此函数调用不会复制。

```python
>>> def f(x):
...     print(id(x))
...
>>> id(a)                           # id is a unique identifier of an object
148293216
>>> f(a)
148293216
```

### View or Shallow Copy

The `view` method creates a new array object that looks at the same data.

```python
>>> c = a.view()
>>> c is a
False
>>> c.base is a                        # c is a view of the data owned by a
True
>>> c.flags.owndata
False
>>>
>>> c.shape = 2,6                      # a's shape doesn't change
>>> a.shape
(3, 4)
>>> c[0,4] = 1234                      # change c, a's data also changes
>>> a
array([[   0,    1,    2,    3],
       [1234,    5,    6,    7],
       [   8,    9,   10,   11]])
```

Slicing an array returns a view of it: 

数组的切片返回数组的view，对切片的修改会修改原data

```python
>>> s = a[ : , 1:3]     # spaces added for clarity; could also be written "s = a[:,1:3]"
>>> s[:] = 10           # s[:] is a view of s. Note the difference between s=10 and s[:]=10
>>> a
array([[   0,   10,   10,    3],
       [1234,   10,   10,    7],
       [   8,   10,   10,   11]])
```

### Deep Copy

The `copy` method makes a complete copy of the array and its data.

```python
>>> d = a.copy()                          # a new array object with new data is created
>>> d is a
False
>>> d.base is a                           # d doesn't share anything with a
False
>>> d[0,0] = 9999
>>> a
array([[   0,   10,   10,    3],
       [1234,   10,   10,    7],
       [   8,   10,   10,   11]])
```

当只需要一个很大的array的一小部分时，可以先切片，然后`copy()`，然后`del`原来的array

```python
>>> a = np.arange(int(1e8))
>>> b = a[:100].copy()
>>> del a  # the memory of ``a`` can be released.
```

如果使用`b = a [：100]`，则a由b引用，并且即使执行`del a`也将保留在内存中。

### Functions and Methods Overview

Array Creation

[`arange`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arange.html#numpy.arange), [`array`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html#numpy.array), [`copy`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.copy.html#numpy.copy), [`empty`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.empty.html#numpy.empty), [`empty_like`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.empty_like.html#numpy.empty_like), [`eye`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.eye.html#numpy.eye), [`fromfile`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fromfile.html#numpy.fromfile), [`fromfunction`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fromfunction.html#numpy.fromfunction), [`identity`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.identity.html#numpy.identity), [`linspace`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.linspace.html#numpy.linspace), [`logspace`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.logspace.html#numpy.logspace), [`mgrid`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mgrid.html#numpy.mgrid),[`ogrid`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ogrid.html#numpy.ogrid), [`ones`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ones.html#numpy.ones), [`ones_like`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ones_like.html#numpy.ones_like), *r*, [`zeros`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros.html#numpy.zeros), [`zeros_like`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros_like.html#numpy.zeros_like)

Conversions

[`ndarray.astype`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.astype.html#numpy.ndarray.astype), [`atleast_1d`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.atleast_1d.html#numpy.atleast_1d), [`atleast_2d`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.atleast_2d.html#numpy.atleast_2d), [`atleast_3d`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.atleast_3d.html#numpy.atleast_3d), [`mat`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mat.html#numpy.mat)

Manipulations

[`array_split`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array_split.html#numpy.array_split), [`column_stack`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.column_stack.html#numpy.column_stack), [`concatenate`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.concatenate.html#numpy.concatenate), [`diagonal`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.diagonal.html#numpy.diagonal), [`dsplit`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.dsplit.html#numpy.dsplit), [`dstack`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.dstack.html#numpy.dstack), [`hsplit`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.hsplit.html#numpy.hsplit), [`hstack`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.hstack.html#numpy.hstack), [`ndarray.item`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.item.html#numpy.ndarray.item), [`newaxis`](https://docs.scipy.org/doc/numpy/reference/constants.html#numpy.newaxis),[`ravel`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ravel.html#numpy.ravel), [`repeat`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.repeat.html#numpy.repeat), [`reshape`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.reshape.html#numpy.reshape), [`resize`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.resize.html#numpy.resize), [`squeeze`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.squeeze.html#numpy.squeeze), [`swapaxes`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.swapaxes.html#numpy.swapaxes), [`take`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.take.html#numpy.take), [`transpose`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.transpose.html#numpy.transpose), [`vsplit`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vsplit.html#numpy.vsplit), [`vstack`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vstack.html#numpy.vstack)

Questions

[`all`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.all.html#numpy.all), [`any`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.any.html#numpy.any), [`nonzero`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nonzero.html#numpy.nonzero), [`where`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.where.html#numpy.where)

Ordering

[`argmax`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argmax.html#numpy.argmax), [`argmin`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argmin.html#numpy.argmin), [`argsort`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argsort.html#numpy.argsort), [`max`](https://docs.python.org/dev/library/functions.html#max), [`min`](https://docs.python.org/dev/library/functions.html#min), [`ptp`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ptp.html#numpy.ptp), [`searchsorted`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.searchsorted.html#numpy.searchsorted), [`sort`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sort.html#numpy.sort)

Operations

[`choose`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.choose.html#numpy.choose), [`compress`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.compress.html#numpy.compress), [`cumprod`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumprod.html#numpy.cumprod), [`cumsum`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumsum.html#numpy.cumsum), [`inner`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.inner.html#numpy.inner), [`ndarray.fill`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.fill.html#numpy.ndarray.fill), [`imag`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.imag.html#numpy.imag), [`prod`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.prod.html#numpy.prod), [`put`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.put.html#numpy.put), [`putmask`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.putmask.html#numpy.putmask), [`real`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.real.html#numpy.real), [`sum`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sum.html#numpy.sum)

Basic Statistics

[`cov`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cov.html#numpy.cov), [`mean`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mean.html#numpy.mean), [`std`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.std.html#numpy.std), [`var`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.var.html#numpy.var)

Basic Linear Algebra

[`cross`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cross.html#numpy.cross), [`dot`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.dot.html#numpy.dot), [`outer`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.outer.html#numpy.outer), [`linalg.svd`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.linalg.svd.html#numpy.linalg.svd), [`vdot`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vdot.html#numpy.vdot)

## Fancy indexing and index tricks

通过整数array和Boolean array进行索引

### Indexing with Arrays of Indices

被索引的array是一维

```python
>>> a = np.arange(12)**2                       # the first 12 square numbers
>>> a
array([  0,   1,   4,   9,  16,  25,  36,  49,  64,  81, 100, 121])
>>> i = np.array( [ 1,1,3,8,5 ] )              # an array of indices
>>> a[i]                                       # the elements of a at the positions i
array([ 1,  1,  9, 64, 25])
>>>
>>> j = np.array( [ [ 3, 4], [ 9, 7 ] ] )      # a bidimensional array of indices
>>> a[j]                                       # the same shape as j
array([[ 9, 16],
       [81, 49]])
```

当被索引的array a是多维时，索引的是a的第一个维度

```python
>>> palette = np.array( [ [0,0,0],                # black
...                       [255,0,0],              # red
...                       [0,255,0],              # green
...                       [0,0,255],              # blue
...                       [255,255,255] ] )       # white
>>> image = np.array( [ [ 0, 1, 2, 0 ],           # each value corresponds to a color in the palette
...                     [ 0, 3, 4, 0 ]  ] )
>>> palette[image]                            # the (2,4,3) color image
array([[[  0,   0,   0],
        [255,   0,   0],
        [  0, 255,   0],
        [  0,   0,   0]],
       [[  0,   0,   0],
        [  0,   0, 255],
        [255, 255, 255],
        [  0,   0,   0]]])
```

索引array是两个shape一样的array时

```python
>>> a = np.arange(12).reshape(3,4)
>>> a
array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])
>>> i = np.array( [ [0,1],                        # indices for the first dim of a
...                 [1,2] ] )
>>> j = np.array( [ [2,1],                        # indices for the second dim
...                 [3,3] ] )
>>>
>>> a[i,j]                                     # i and j must have equal shape
array([[ 2,  5],
       [ 7, 11]])
>>>
>>> a[i,2]
array([[ 2,  6],
       [ 6, 10]])
>>>
>>> a[:,j]                                     # i.e., a[ : , j]
array([[[ 2,  1],
        [ 3,  3]],
       [[ 6,  5],
        [ 7,  7]],
       [[10,  9],
        [11, 11]]])
```

也可以使用list作为索引array

```python
>>> l = [i,j]
>>> a[l]                                       # equivalent to a[i,j]
array([[ 2,  5],
       [ 7, 11]])
```



```python
>>> s = np.array( [i,j] )
>>> s
array([[[0, 1],
        [1, 2]],

       [[2, 1],
        [3, 3]]])
>>> a[s]                                       # not what we want
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
IndexError: index (3) out of range (0<=index<=2) in dimension 0
>>>
>>> a[tuple(s)]                                # same as a[i,j]
array([[ 2,  5],
       [ 7, 11]])
```

the search of the maximum value of time-dependent series

```
>>> time = np.linspace(20, 145, 5)                 # time scale
>>> data = np.sin(np.arange(20)).reshape(5,4)      # 4 time-dependent series
>>> time
array([  20.  ,   51.25,   82.5 ,  113.75,  145.  ])
>>> data
array([[ 0.        ,  0.84147098,  0.90929743,  0.14112001],
       [-0.7568025 , -0.95892427, -0.2794155 ,  0.6569866 ],
       [ 0.98935825,  0.41211849, -0.54402111, -0.99999021],
       [-0.53657292,  0.42016704,  0.99060736,  0.65028784],
       [-0.28790332, -0.96139749, -0.75098725,  0.14987721]])
>>>
>>> ind = data.argmax(axis=0)                  # index of the maxima for each series
>>> ind
array([2, 0, 3, 1])
>>>
>>> time_max = time[ind]                       # times corresponding to the maxima
>>>
>>> data_max = data[ind, range(data.shape[1])] # => data[ind[0],0], data[ind[1],1]...
>>>
>>> time_max
array([  82.5 ,   20.  ,  113.75,   51.25])
>>> data_max
array([ 0.98935825,  0.84147098,  0.99060736,  0.6569866 ])
>>>
>>> np.all(data_max == data.max(axis=0))
True
```

assign

```python
>>> a = np.arange(5)
>>> a
array([0, 1, 2, 3, 4])
>>> a[[1,3,4]] = 0
>>> a
array([0, 0, 2, 0, 0])

>>> a = np.arange(5)
>>> a[[0,0,2]]=[1,2,3] # 重复赋值，取最后赋的值
>>> a
array([2, 1, 3, 3, 4])

>>> a = np.arange(5)
>>> a[[0,0,2]]+=1 # a[[0,0,2]]=a[[0,0,2]]+1 This is because Python requires “a+=1” to be equivalent to “a = a + 1”.

# solve 
bbins = np.bincount([0,0,2])
a[:len(bbins)] += bbins

>>> a
array([1, 1, 3, 3, 4])
```

### Indexing with Boolean Arrays

```python
>>> a = np.arange(12).reshape(3,4)
>>> b = a > 4
>>> b                                          # b is a boolean with a's shape
array([[False, False, False, False],
       [False,  True,  True,  True],
       [ True,  True,  True,  True]])
>>> a[b]                                       # 1d array with the selected elements
array([ 5,  6,  7,  8,  9, 10, 11])

>>> a[b] = 0                                   # All elements of 'a' higher than 4 become 0
>>> a
array([[0, 1, 2, 3],
       [4, 0, 0, 0],
       [0, 0, 0, 0]])

>>> a = np.arange(12).reshape(3,4)
>>> b1 = np.array([False,True,True])             # first dim selection
>>> b2 = np.array([True,False,True,False])       # second dim selection
>>>
>>> a[b1,:]                                   # selecting rows
array([[ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])
>>>
>>> a[b1]                                     # same thing
array([[ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])
>>>
>>> a[:,b2]                                   # selecting columns
array([[ 0,  2],
       [ 4,  6],
       [ 8, 10]])
>>>
>>> a[b1,b2]                                  # a weird thing to do why?
array([ 4, 10])
```

### The ix_() function

The [`ix_`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ix_.html#numpy.ix_) function can be used to combine different vectors so as to obtain the result for each n-uplet. 

```python
>>> a = np.array([2,3,4,5])
>>> b = np.array([8,5,4])
>>> c = np.array([5,4,6,8,3])
>>> ax,bx,cx = np.ix_(a,b,c)
>>> ax
array([[[2]],
       [[3]],
       [[4]],
       [[5]]])
>>> bx
array([[[8],
        [5],
        [4]]])
>>> cx
array([[[5, 4, 6, 8, 3]]])
>>> ax.shape, bx.shape, cx.shape
((4, 1, 1), (1, 3, 1), (1, 1, 5))
>>> result = ax+bx*cx
>>> result
array([[[42, 34, 50, 66, 26],
        [27, 22, 32, 42, 17],
        [22, 18, 26, 34, 14]],
       [[43, 35, 51, 67, 27],
        [28, 23, 33, 43, 18],
        [23, 19, 27, 35, 15]],
       [[44, 36, 52, 68, 28],
        [29, 24, 34, 44, 19],
        [24, 20, 28, 36, 16]],
       [[45, 37, 53, 69, 29],
        [30, 25, 35, 45, 20],
        [25, 21, 29, 37, 17]]])
>>> result[3,2,4]
17
>>> a[3]+b[2]*c[4]
17
```

### Indexing with strings

See [Structured arrays](https://docs.scipy.org/doc/numpy/user/basics.rec.html#structured-arrays).

## Linear Algebra

### Simple Array Operations

```python
>>> import numpy as np
>>> a = np.array([[1.0, 2.0], [3.0, 4.0]])
>>> print(a)
[[ 1.  2.]
 [ 3.  4.]]

>>> a.transpose()
array([[ 1.,  3.],
       [ 2.,  4.]])

>>> np.linalg.inv(a)
array([[-2. ,  1. ],
       [ 1.5, -0.5]])

>>> u = np.eye(2) # unit 2x2 matrix; "eye" represents "I"
>>> u
array([[ 1.,  0.],
       [ 0.,  1.]])
>>> j = np.array([[0.0, -1.0], [1.0, 0.0]])

>>> j @ j        # matrix product
array([[-1.,  0.],
       [ 0., -1.]])

>>> np.trace(u)  # trace
2.0

>>> y = np.array([[5.], [7.]])
>>> np.linalg.solve(a, y)
array([[-3.],
       [ 4.]])

>>> np.linalg.eig(j)
(array([ 0.+1.j,  0.-1.j]), array([[ 0.70710678+0.j        ,  0.70710678-0.j        ],
       [ 0.00000000-0.70710678j,  0.00000000+0.70710678j]]))
```

## Finding Documentation

```python
>>> help(obj) 
>>> np.info(obj)
>>> dir(obj)
```

