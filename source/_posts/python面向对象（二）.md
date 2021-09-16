---
title: python面向对象（二）
date: 2021-04-29 14:40:25
type: "_posts"
layout: "posts"
---
# python面向对象

抽象类：作为父类存在，一旦对象化会报错，python3.8可对象化。抽象函数定义在抽象类中，子类必须重写该函数才能使用，相应的抽象函数，则是使用装饰器@abstractmethod来表示。

抽象类是一种自上而下的设计风范，只需要用少量的代码描述清楚要做的事情，定义好接口。

```python
from abc import ABCMeta,abstractmethod

class Entity():
    @abstractmethod
    def get_title(self):
        pass
    @abstractmethod
    def set_title(self,title):
        pass
class Document(Entity):
    def get_title(self):
        return self.title
    def set_title(self,title):
        self.title = title
document = Document()
document.set_title('Harry Potter')
print(document.get_title())
entity = Entity()
print(entity)
entity.set_title('Test')
print(entity.get_title())


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
Harry Potter
<__main__.Entity object at 0x000001F705F966A0>
None

Process finished with exit code 0
```

面向对象的四要素：类、属性、对象、函数（方法）

类：具有相同属性和函数（方法）的对象（实例）的集合。

```python
多继承，构造函数的执行顺序：

class A():
    def __init__(self):
        print('enter A')
        print('leave A')
class B(A):
    def __init__(self):
        print('enter B')
        super().__init__()
        print('leave B')
class C(A):
    def __init__(self):
        print('enter C')
        super().__init__()
        print('leave C')
class D(B,C):
    def __init__(self):
        print('enter D')
        super().__init__()
        print('leave D')
D()

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
enter D
enter B
enter C
enter A
leave A
leave C
leave B
leave D

Process finished with exit code 0
```

## 实现一个搜索引擎

```
一个搜索引擎由搜索器、索引器、检索器和用户接口四个部分组成。
```

# python模块化

## 简单模块化

```python
简单模块化

同一文件夹：
	将函数、类、常量拆分到不同的文件，把它们放在同一个文件夹，然后使用from  your_file import function_name,class_name的方法调用。
不同文件夹：
	导入：from 文件夹名.文件名 import *
    	 from 文件夹名.文件名 import 函数名
如果想要调用上层目录，可以使用 import sys,   sys.path.append("..")表示将当前程序所在位置向上提了一级，之后就可以调用上一层的文件夹中的模块了。（不推荐使用）

#utils.py

def get_sum(a,b):
    return a + b

#class_utils.py

class Encoder(object):
    def encode(self,s):
        return s[::-1]      #倒序
class Decoder(object):
    def decode(self,s):
        return ''.join(reversed(list(s)))   #revesed()，倒排
        
#main_s.py

from utils import get_sum
from class_utils import *
print(get_sum(1,2))
encoder = Encoder()
decoder = Decoder()
print(encoder.encode('abcde'))
print(decoder.decode('edcba'))

D:\Enviroments\python\python\python3.exe D:/python_project/jike/main.py
3
edcba
abcde

Process finished with exit code 0
```

## 项目模块化

```
所有代码放在同一个仓库的优点：
1、简化依赖管理，所有的代码模块都可以被调用，提高代码的分享共用能力
2、版本统一。
3、代码追溯。

项目模块化：以项目的根目录作为最基本的目录，所有模块的调用，都要通过根目录一层层向下索引的方式来import。
```

```python
#proto/mat.py

class Matrix(object):
    def __init__(self,data):
        self.data = data		#数据
        self.n = len(data)		#行
        self.m = len(data[0])	#列
        
#utils/mat_mul.py

from proto.mat import Matrix
def mat_mul(matrix_1,matrix_2:Matrix):		#matrix_1,matrix_2是参数,Matrix是参数类型
    assert matrix_1.m == matrix_2.n			#矩阵1的列号和矩阵2的行号相等
    n,m,s = matrix_1.n,matrix_1.m,matrix_2.m
    result = [[0 for _ in range(n)] for _ in range(s)]
    for i in range(n):
        for j in range(s):
            for k in range(m):
                result[i][k] += matrix_1.data[i][j] * matrix_2.data[j][k]	#矩阵相乘
    return Matrix(result)

#jike/main_s.py

from proto.mat import Matrix
from utils.mat_mul import mat_mul
a = Matrix([[1,2],[3,4]])
b = Matrix([[5,6],[7,8]])
print(mat_mul(a,b).data)

main_s.py执行结果：

D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
[[19, 22], [43, 50]]

Process finished with exit code 0
        
```

```python
if __name__ == '__main__'
import 在导入文件时，会自动把所有暴露在外面的代码全都执行一遍，因此，如果想要把一个东西封装成模块，又想让它可以执行的话，就必须将要执行的代码放在if __name__ == '__main__'下面。

if __name__ == '__main__'可以来避开import时执行。
```

```python
#utils/utils.py

def get_sum(a,b):
    return a + b
print('testing')
print('{} + {} = {}'.format(1,2,get_sum(1,2)))

#utils/utils_with_main.py

def get_sum(a, b):
    return a + b


if __name__ == '__main__':
    print('testing')
    print('{} + {} = {}'.format(1, 2, get_sum(1, 2)))

#main_s.py

from utils.utils import *
print('get_sum:',get_sum(1,2))

执行结果：
D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
testing
1 + 2 = 3
get_sum: 3

Process finished with exit code 0

from utils.utils_with_main import *
print('get_sum:',get_sum(1,2))

执行结果：
D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
get_sum: 3

Process finished with exit code 0
```

```python
from moudle_name import * 和 import moudle_name 的区别：

from moudle_name import * 会把moudle中所有的函数和类全拿过来，如果和其他函数名冲突就会出现问题；import moudle_name也会导入所有的函数和类，但是调用的时候必须使用moudle_name.func的方法调用，等于增加了一层layer，有效避免冲突。
```

# python对象的比较、拷贝

## "== "vs "is"

```python
== 比较两个对象之间的值是否相等
is 比较两个对象的身份标识是否相等，是否是同一对象，是否指向同一个内存地址

is的效率优于'=='，因为'is'操作无法被重载，执行'is'操作只是简单的获取对象ID，并进行比较；
而'=='操作符则会递归遍历对象所有值，并逐一比较。

a = 10
b = 10
print(a == b)
print(id(a))    #id(object)函数，获取对象的身份标识，对于int类型的数据，a is b为True的结论只适用于-5到256范围内的数字，因为python内部对-5到256的整型数据维持一个数组，起到一个缓存作用。
print(id(b))
print(a is b)

D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
True
140712789907392
140712789907392
True

Process finished with exit code 0


'''
对于不可变的变量，之前用 == 或 is 比较后，结果不会一直不变
'''
t1 = (1,2,[3,4])
t2 = (1,2,[3,4])
print(t1 == t2)
t1[-1].append(5)    #元组中的列表是可变的，修改元组中的列表，元组也随之改变
print(t1)
print(t1 == t2)

D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
True
(1, 2, [3, 4, 5])
False

Process finished with exit code 0
```

## 浅拷贝和深度拷贝

**浅拷贝**

常见的浅拷贝的方法，是使用数据类型本身的构造器。

```python
l1 = [1,2,3]
l2 = list(l1)
print(l1 == l2)     #True
print(l1 is l2)     #False
s1 = set([1,2,3])       
s2 = set(s1)
print(s1 == s2)     #True
print(s1 is s2)     #False
print(s2)           #{1, 2, 3}
'''
对于可变的序列，还可以通过切片操作符':'完成浅拷贝
'''
l11 = [1,2,3]
l12 = l11[:]
print(l11 == l12)       #True
print(l11 is l12)       #False
```

python中也提供了相应的函数copy.copy()，适用于任何数据类型。

```python
import copy
l1 = [1,2,3]
l2 = l1.copy()
print(l2)
#l2 = copy.copy(l1)     作用相同  l1.copy()
print(l1 == l2)     #True
print(l1 is l2)     #False


D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
[1, 2, 3]
True
False

Process finished with exit code 0
```

**注意**

```python
对于元组，使用tuple()或切片操作符':'不会创建一份浅拷贝，相反，它会返回一个指向相同元组的引用。
```

```python
l1 = (1,2,3)
l2 = tuple(l1)
l3 = l1[:]
print(l1 == l2 == l3)
print(l1 == l2 == l3)


D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
True
True

Process finished with exit code 0
```

```python
浅拷贝：指重新分配一块内存，创建一个新的对象，里面的元素是原对象中子对象的引用。因此，若原对象中的元素不可变，无所谓；但如果元素可变，浅拷贝通常会带来一些副作用。

'''
由于浅拷贝里的元素是对原对象元素的引用，
所以l2中的元素和l1指向同一个列表和元组对象。
'''
l1 = [(1,2),[30,40]]
l2 = list(l1)
l1.append(100)  #l1新增元素不会影响l2，l1和l2作为两个整体对象不共享内存地址
l1[1].append(50)    #l2也会改变，因为l2中的列表和l1指向同一个列表
print(l1)
print(l2)
l1[0] += (3,4)  #元组不可变，l1创建了新元组，l2没有引用新的元组
print(l1)
print(l2)

D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
[(1, 2), [30, 40, 50], 100]
[(1, 2), [30, 40, 50]]
[(1, 2, 3, 4), [30, 40, 50], 100]
[(1, 2), [30, 40, 50]]

Process finished with exit code 0
```

**深拷贝**

```python
深拷贝：指重新分配一块内存，创建一个新的对象，并且将原对象中的元素，以递归的方式，通过创建新的子对象拷贝到新对象中。因此，原对象和新对象没有任何关联。
python中以copy.deepcopy()来实现对象的深度拷贝。

import copy
l1 = [(1,2),[30,40]]
l2 = copy.deepcopy(l1)
l1.append(100)
l1[1].append(50)
l1[0] += (3,4)
print(l1)
print(l2)


D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
[(1, 2, 3, 4), [30, 40, 50], 100]
[(1, 2), [30, 40]]

Process finished with exit code 0


无限循环问题：深拷贝中会维护一个字典，记录已经拷贝的对象及其ID，来提高效率并防止无限递归的发生。
import copy
l1 = [(1,2),[30,40]]
l1.append(l1)       #列表l1中有指向自身的引用，因此l1是一个无限嵌套的列表
l2 = copy.deepcopy(l1)
print(l1)
print(l2)


D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
[(1, 2), [30, 40], [...]]
[(1, 2), [30, 40], [...]]

Process finished with exit code 0
```

```python
'''
无限嵌套的列表，执行‘==’操作时，逐个比较列表中的元素，递归层数是无限的，会报错。
'''
import copy
l1 = [(1,2),[30,40]]
l1.append(l1)       #列表l1中有指向自身的引用，因此l1是一个无限嵌套的列表
l2 = copy.deepcopy(l1)
print(l1)
print(l2)
print(l1 is l2)
print(l1 == l2)



D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
[(1, 2), [30, 40], [...]]
[(1, 2), [30, 40], [...]]
False
Traceback (most recent call last):
  File "D:\python_project\jike\main_s.py", line 7, in <module>
    print(l1 == l2)
RecursionError: maximum recursion depth exceeded in comparison

Process finished with exit code 1
```

# python中参数的传递

**值传递**

```python
值传递：拷贝参数的值，然后传递给函数里的新变量，这样，原变量和新变量之间相互独立，互不影响。
```

**引用传递**

```python
引用传递：指把参数的引用传给新的变量，这样，原变量和新变量指向同一块内存地址，如果改变了其中任何一个变量的值，那么另外一个变量也会相应地随之改变。
```

## python变量及其赋值

```
1、变量的赋值，只是表示让变量指向了某个对象，并不表示拷贝对象给变量；一个对象可以被多个变量所指向
2、可变对象（列表、字典、集合等）的改变，会影响所有指向该对象的变量
3、对于不可变对象（字符串、整型、元组等），所有指向该对象的变量的值总是一样的，也不会改变。但是通过某些操作（+=等等）更新不可变对象的值时，会返回一个新的对象。
4、变量可以被删除，但是对象无法被删除。（垃圾回收）
```

```python
a = 1
b = a
a += 1
print(a)
print(b)
l1 = [1,2,3]
l2 = l1
l1.append(4)
print(l1)
print(l2)

D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
2
1
[1, 2, 3, 4]
[1, 2, 3, 4]

Process finished with exit code 0
```

## python函数的参数传递

```
python的参数传递是赋值传递，或叫做对象的引用传递。python里所有的数据类型都是对象，所以参数传递时，只是让新变量与原变量指向相同的对象而已，并不存在值传递或是引用传递一说。
```

```python
def func_1(a):
    b = 2
    return b
a = 1
a = func_1(a)   #重新赋值
print(a)

def func_2(l):
    l.append(4)
l1 = [1,2,3]
func_2(l1)
print(l1)

def func_3(l2):
    l2 = l2 + [3,4] #创建了末尾加入[3,4]的新列表，l2 重新赋值指向新列表
l3 = [1,2]
func_3(l3)
print(l3)

D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
2
[1, 2, 3, 4]
[1, 2]

Process finished with exit code 0
```

```
python中参数的传递是赋值传递，或叫做对象的引用传递。这里的赋值或对象的引用传递，不是指向一个具体的内存地址，而是指向一个具体的对象。

修改变量的值有两种方法：
1、直接将可变数据类型（字典、列表、集合等）当参数传入，直接在其上修改；
2、创建一个新的变量，来保存修改后的值，然后将其返回给原变量。（推荐）
```

```python
l1 = [1,2,3]
l2 = [1,2,3]
l3 = l2
print(id(l1))
print(id(l2))
print(id(l3))


D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
2792886690112
2792887381440
2792887381440

Process finished with exit code 0
```

```python
def func(d):    #字典是可变的，参数中值被改变，字典中key对应的值也随之改变
    d['a'] = 10
    d['b'] = 20
d = {'a':1,'b':2}
func(d)
print(d)


D:\Enviroments\python\python\python3.exe D:\python_project\jike\main_s.py
{'a': 10, 'b': 20}

Process finished with exit code 0
```

