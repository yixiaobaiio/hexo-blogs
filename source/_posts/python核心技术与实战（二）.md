---
title: python核心技术与实战（二）
date: 2021-04-29 14:40:25
type: "_posts"
layout: "posts"
---
# python核心技术与实战（二）

## 04 输入输出

### 1、键盘输入输出

```
input()函数暂停程序运行，同时等待键盘输入，直到回车键被按下；函数的参数即为提示语，输入的类型永远是字符型（str）。
print()函数则接受字符串、数字、字典、列表甚至一些自定义类型的输出。
python对int类型没有最大限制，但对float类型有精度限制。
```

### 2、文件输入输出

```python
#读取文件内容到列表中
f = open(file='./score',encoding='utf8')
info = f.readlines()
f.close()
print(info)
#计算总成绩
for i in range(len(info)):
    if i == 0:  # info[i]='姓名        系统测试       数据库     linux\n'
        info[i] = info[i].strip()+'\t\t总成绩\n'
        #print(info[i])
    else:
        tmp = info[i].strip().split()   #['a1','80','87','78']
        s = int(tmp[1]) + int(tmp[2]) +int(tmp[3])
        tmp.append(str(s))
        info[i] = '\t\t'.join(tmp)+'\n'
print(info)
#将处理后的内容覆盖写入文件
f = open(file='./score',mode='w',encoding='utf8')
f.writelines(info)
f.close()

with语句不需要显示调用close()函数，能够在任务执行完毕后自动执行关闭文件操作。
```

### 3、json序列化与实战

```python
import json
params = {
    'symbol':'123456',
    'type':'limit',
    'price':123.4,
    'amount':23
}
params_str = json.dumps(params)     #接受python基本数据类型，将其序列化为string
print('after json serialization')
print('type of params_str = {},params_str={}'.format(type(params_str),params))
print('************************')
original_params = json.loads(params_str)        #接受一个合法字符串，将其反序列化为Python的基本数据类型
print('after json deserialization')
print('type of original_params={},original_params={}'.format(type(original_params),original_params))


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
after json serialization
type of params_str = <class 'str'>,params_str={'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}
************************
after json deserialization
type of original_params=<class 'dict'>,original_params={'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}

Process finished with exit code 0
```

**输入字符串到文件，从文件读取json字符串**

```python
import json
params = {
    'symbol':'123456',
    'type':'limit',
    'price':123.4,
    'amount':23
}
with open('params.json','w') as fout:
    params_str = json.dump(params,fout) #接受python基本数据类型，将其序列化为string
#params_str = json.dumps(params)
print('after json serialization')
print('type of params_str = {},params_str={}'.format(type(params_str),params))
print('************************')
with open('params.json','r') as fin:
    original_params = json.load(fin)        #接受一个合法字符串，将其反序列化为Python的基本数据类型
print('after json deserialization')
print('type of original_params={},original_params={}'.format(type(original_params),original_params))


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
after json serialization
type of params_str = <class 'NoneType'>,params_str={'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}
************************
after json deserialization
type of original_params=<class 'dict'>,original_params={'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}

Process finished with exit code 0
```

总结：

1、I/O操作要谨慎，一定要进行充分的错误处理，并细心编码，防止出现编码漏洞；

2、编码时，对内存占用和磁盘占用要有充分的估计，这样在出错时可以更容易找到原因。

## 05 条件与循环2

```python
#条件
python不支持switch语句，多条件判断时，只能使用if...elif...else
```

循环

```python
python中的数据结构只要是可迭代的，都可以利用for循环遍历。
字典本身只有键是可迭代的，如果要遍历它的值或者键值对，需要通过其内置函数values()或items()实现。values()返回字典值的集合，items()返回键值对的集合。

params = {'symbol':'123456','type':'limit','price':123.4,'amount':23}
for k in params:    #遍历字典的键
    print(k)
for v in params.values():   #遍历字典的值
    print(v)
for w,n in params.items():    #遍历字典的键值对
    print('key:{},value:{}'.format(w,n))
    
D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
symbol
type
price
amount
123456
limit
123.4
23
key:symbol,value:123456
key:type,value:limit
key:price,value:123.4
key:amount,value:23

Process finished with exit code 0


集合遍历
set1 = {1,2,3,4,5,6}
for i in set1:
    print(i)
```

```python
python内置函数enumerate()，遍历数据时，不仅返回每个元素，还返回其对应的索引。

set1 = {1,2,3,4,5,6}
for index,item in enumerate(set1):
    if index < 3:
        print(index,item)
        
D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
0 1
1 2
2 3

Process finished with exit code 0
```

### **条件与循环的复用**

```python
[(xx,yy) for xx in x for yy in y if xx != yy]

等价于：
l = []
for xx in x:
	for yy in y:
		if xx != yy:
			l.append((xx,yy))
```

```python
attributes = ['name','dob','gender']
values = [['jason','2000-02-01','male'],['mike','1999-01-01','male'],
          ['nancy','2001-02-01','female']]
#多条件循环
l = []
for value in values:
    dict = {}
    for i in range(0,len(value)):
        dict[attributes[i]] = value[i]
    l.append(dict)
print(l)
#条件循环的复用  一行代码
li = [{key:value[index] for index,key in enumerate(attributes)} for value in values]
print(li)
或
li = [dict(zip(attributes,value)) for value in values]

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
[{'name': 'jason', 'dob': '2000-02-01', 'gender': 'male'}, {'name': 'mike', 'dob': '1999-01-01', 'gender': 'male'}, {'name': 'nancy', 'dob': '2001-02-01', 'gender': 'female'}]

Process finished with exit code 0
```

## 06 异常处理

```
except  Exception :匹配任意非系统异常
except:		匹配任意异常（包括系统异常）
当程序存在多个except block时，最多只有一个被执行，即如果多个except声明的异常都与实际相匹配，只有最前面的except block会被执行，其他则被忽略。
```

### 用户自定义异常

```python
class MyInputError(Exception):
    def __init__(self,value):   #自定义异常类型的初始化
        self.value = value
    def __str__(self):      #自定义异常类型的string表达形式
        return ('{} is invalid input'.format(repr(self.value)))
try:
    raise MyInputError(1)   #抛出MyInputError这个异常
except MyInputError as err:
    print('error:{}'.format(err))


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
error:1 is invalid input

Process finished with exit code 0
```

### 异常的使用场景与注意点

```
1、如果不确定某段代码能否成功执行，往往这个地方就需要使用异常处理。
2、对于流程控制（flow-control）的代码逻辑，一般不用异常处理。
```

## 07 函数

### 函数基础

```python
1）函数：就是为了实现某一功能的代码段，只要写好以后，就可以重复利用。
2）def 是可执行语句，意味着函数直到被调用前，都是不存在的，当程序调用函数时，def语句才会创建一个新的函数对象，并赋予其名字。

3）主程序调用函数时，必须保证这个函数此前已经定义过，不然就会报错。

4）在函数内部调用其他函数，函数间哪个声明在前，哪个声明在后都无所谓，因为def是可执行语句，函数在调用前都不存在，只需要保证在调用时，所需函数都已经声明定义就可以了。

def my_func(message):
    my_sub_func(message)

def my_sub_func(message):
    print('Got a message:{}'.format(message))
my_func('hello world')

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
Got a message:hello world

Process finished with exit code 0


5）python函数的参数可以设定默认值，如果参数没有传参，就会使用默认参数
def my_func(message = 'Hello'):
    my_sub_func(message)

def my_sub_func(message):
    print('Got a message:{}'.format(message))
my_func()


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
Got a message:Hello

Process finished with exit code 0
```

**多态**：python中不用考虑输入的数据类型，而是将其交给具体的代码去判断执行，同样的一个函数（如：my_sum()，可以同时应用在整型、列表、字符串等等操作中。）

```python
def my_sum(a,b):
   return a + b

t = my_sum(1,3)
print(t)
s = my_sum('hello','world')
print(s)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
4
helloworld

Process finished with exit code 0
```

python支持函数的嵌套，就是指函数里又有函数。

### **函数变量的作用域**

对于嵌套函数，内部函数可以访问外部函数定义的变量，但是无法修改，若要修改，必须加上**nonlocal**关键字。

如果不加上nonlocal这个关键字，而内部函数的变量又和外部函数变量同名，那么内部函数变量会覆盖外部函数的变量。

嵌套函数作用：保证数据的隐私性，提高程序的运行效率。

```python
def outer():
    x = 'local'
    y = 3

    def inner():
        nonlocal x
        x = 'nonlocal'
        y = 6
        print(x)
        print(y)

    inner()
    print('outer:', y)


outer()


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
nonlocal
6
outer: 3

Process finished with exit code 0
```

### 闭包(closure)

```python
闭包：与嵌套函数类似，不同的是这里的外部函数返回的是一个函数，而不是一个具体的值，返回的函数通常赋予一个变量，这个变量可以在后面被继续执行调用。
作用：
1、让程序变得更简单易读
2、减少多次调用导致的不必要的开销，提高程序的运行效率

闭包常常和装饰器一起使用。

def nth_power(exponent):
    def exponent_of(base):
        return base ** exponent
    return exponent_of  #返回值是exponent_of函数
square = nth_power(2)   #计算一个数的平方
cube = nth_power(3) #计算一个数的立方

print(square(6))
print(cube(6))

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
36
216

Process finished with exit code 0
```

### 匿名函数

```python
匿名函数与常规函数的区别：
1、lambda是一个表达式，而不是一个语句
		表达式：用一系列的‘公式’去表达一个东西
		语句：就是一定完成了某些功能，如：赋值语句
	2、lambda可以用在一些常规函数def不能用的地方，如：列表内部
	3、lambda可以用作某些函数的参数，常规函数def也不能
2、lambda的主体是只有一行的简单表达式，并不能扩展成一个多行的代码块。

li = [(lambda x:x*x)(x) for x in range(0,10)]   #用在列表内部
print(li)
#用作函数的参数
l2 = [(12,12),(25,26),(46,31),(32,20),(21,36)]
l2.sort(key=lambda x:x[1])
print(l2)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
[(12, 12), (32, 20), (25, 26), (46, 31), (21, 36)]

Process finished with exit code 0
```

匿名函数的作用：

适用场景：函数非常简短，只需一行就能完成，且它在程序中只被调用一次。

简化代码的复杂度，提高代码的可读性。

### python函数式编程

```python
函数式编程：指代码中的每一块都是不可变的，都由纯函数的形式组成。这里的纯函数，是指函数本身相互独立，互不影响，对于相同的输入，总会有相同的输出，没有任何副作用。

函数式编程的优缺点：
优点：主要在于其纯函数和不可变的特性使程序更加健壮，易于调试、测试。
缺点：限制多，难写。

def multy_1(l): #非纯函数，调用后l值改变，每次调用l都不同
    for i in range(0,len(l)):
        l[i] *= 2
    return l

def multy_2(l): #纯函数，l未改变，每次调用执行结果相同
    new_list = []
    for i in l:
        new_list.append(i * 2)
    return new_list
```

```python
from functools import reduce

l = [1,2,3,4,5]
'''
map(function,iterable)函数
表示对iterable中的每个元素，都用function这个函数，
最后返回一个新的可遍历的集合。
'''
new_list = map(lambda x:x *2,l)
for i in new_list:
    print(i,end='\t')
print()
'''
filter(function,iterable)函数
和map函数类似，function表示一个函数对象，
filter()函数表示对iterable中每一个元素，
都使用function判断，并返回True或False，
最后将返回True的元素组成一个新的可遍历的集合。
'''
new_list1 = filter(lambda x:x % 2 == 0,l)
for i in new_list1:
    print(i,end='\t')
print()
'''
reduce(function,iterable)函数
通常用来对一个集合做一些累积操作。
表示对iterable的每个元素以及上一次调用后的结果，
运用function进行计算，
所以最后返回一个单独的数值。
'''
produce = reduce(lambda x,y:x * y,l)
print(produce)


D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
2	4	6	8	10	
2	4	
120

Process finished with exit code 0
```

对一个字典，根据值由高到低排序。

```python
d = {'nike':10,'lucy':2,'ben':30}
d1 = sorted(d.items(),key=lambda x:x[1],reverse=True)
print(d1)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/json_1.py
[('ben', 30), ('nike', 10), ('lucy', 2)]

Process finished with exit code 0
```



