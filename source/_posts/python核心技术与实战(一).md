---
title: python核心技术与实战（一）
date: 2021-04-29 14:40:25
type: "_posts"
layout: "posts"
---
# python核心技术与实战

## 01 列表（list）和元组（tuple）

### 基础介绍

列表和元组都是**可以放置任意数据类型的有序集合**。

python中列表和元组中的数据**类型不需要必须一致**。

```python
l = [1,2,'hello','world']	#列表含int和string类型元素
print(l)
tup = ('json',22)	#元组含int和string类型元素
print(tup)
```

```
列表和元组的区别：
1、列表，动态的，长度大小不固定，可随意增、删或改变元素。
2、元组，静态的，长度大小固定，无法增、删或修改。
想要对已有的元组进行修改，需要重新开辟一块内存，创建新的元组。而列表是修改原来列表中的元素，不会创建新的列表。
```

```python
l = [1,2,'hello','world']
l[3] = 40
print(l)
tup = ('json',22)
tup[1] = 16
print(tup)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
[1, 2, 'hello', 40]
Traceback (most recent call last):
  File "D:/python_project/jike/list_tuple.py", line 5, in <module>
    tup[1] = 16
TypeError: 'tuple' object does not support item assignment

Process finished with exit code 1
```

```python
l = [1,2,3,4]
l.append(5)	#添加元素5到原来的列表末尾
print(l)
tup = (1,2,3,4)
new_tup = tup +(5,)	#创建新的new_tup，并依次填充原元组的值
print(new_tup)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
[1, 2, 3, 4, 5]
(1, 2, 3, 4, 5)

Process finished with exit code 0
```

### 基本操作和注意事项

1、Python中的**列表和元组都支持负数索引**。-1表示最后一个元素，-2表示倒数第二个元素，以此类推。

```python
l = [1,2,3,4]
l.append(5)
print(l[-1])
tup = (1,2,3,4)
new_tup = tup +(5,)
print(new_tup[-2])

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
5
4

Process finished with exit code 0
```

2、**列表和元组都支持切片操作。**

```python
l = [1,2,3,4]
l.append(5)
print(l[1:3])   #返回列表中索引从1到2的子列表
tup = (1,2,3,4)
new_tup = tup +(5,)
print(new_tup[1:3]) #返回元组中索引从1到2的子元组

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
[2, 3]
(2, 3)

Process finished with exit code 0
```

3、**列表和元组可以随意嵌套。**

```python
l = [1,2,[2,3],(1,2,3)]
print(l)
tup = (1,2,[1,2],(1,2,3))
print(tup)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
[1, 2, [2, 3], (1, 2, 3)]
(1, 2, [1, 2], (1, 2, 3))

Process finished with exit code 0
```

4、两者之间可以**通过list()和tuple()函数互相转换。**

```python
l = [1,2,[2,3],(1,2,3)]
print(l)

print(tuple(l))
tup = (1,2,[1,2],(1,2,3))
print(tup)

print(list(tup))

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
[1, 2, [2, 3], (1, 2, 3)]
(1, 2, [2, 3], (1, 2, 3))
(1, 2, [1, 2], (1, 2, 3))
[1, 2, [1, 2], (1, 2, 3)]

Process finished with exit code 0
```

**5、列表和元组常用的内置函数**

```python
'''
count(item):表示统计列表/元组中item出现的次数
index(item):表示返回列表/元组中item第一次出现的索引
list.reverse()和list.sort()：表示原地倒转和排序（元组中没有这两个内置的函数）
reversed()和sorted():同样表示对列表/元组进行倒转和排序，
reversed()返回一个倒转后的迭代器，sorted()返回排好序的新列表
'''
l = [1,2,3,1,2,3]
print(l.count(1))   
print(l.index(2))
l.reverse()
print(l)
l.sort()
print(l)

tup = (1,2,1,2,1,2,3)
print(tup.count(3))
print(tup.index(2))
print(list(reversed(tup)))
print(sorted(tup))

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
2
1
[3, 2, 1, 3, 2, 1]
[1, 1, 2, 2, 3, 3]
1
1
[3, 2, 1, 2, 1, 2, 1]
[1, 1, 1, 2, 2, 2, 3]

Process finished with exit code 0

```

### 列表和元组存储方式的差异

```python
'''
放置相同的元素，元组比列表的存储空间少16字节
列表是动态的，需要存放指针来指向对应的元素，（对于int类型，8字节）
此外，由于列表可变，需要额外存储已经分配的长度大小（8字节），这样才可以
实时追踪列表空间的使用情况，当空间不足时，及时分配额外空间
当空间不足时，每次分配空间会额外多分配一些空间：保证其操作的高效性
增加/删除的时间复杂度均为O(1)

元组长度大小固定，元素不可变，存储空间固定。

元组的性能速度略优于列表：python对静态数据做一些资源缓存。初始化操作元组速度优于列表，索引操作两者的差异可忽略不计
'''
l = [1,2]
print(l.__sizeof__())

l.append(3)
print(l.__sizeof__())   #（88-56）/8 = 4个元素的存储空间
l.append(4)
print(l.__sizeof__())

tup = (1,2)
print(tup.__sizeof__())

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
56
88
88
40

Process finished with exit code 0
```

### 列表和元组的使用场景

1、若存储的数据和数量不变，适合使用元组

2、若存储的数据或数量是可变的，适合选择列表

```python
创建空列表，[]比list()效率高

import timeit

print(timeit.timeit('a = list()'))
print(timeit.timeit('a = []'))

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
0.0663261
0.0209299

Process finished with exit code 0
```

## 02 字典和集合

### 字典（dict）和集合（set）基础

字典：**一系列由键(key)和值(value)配对组成的元素的集合**，在python3.7+，字典被确定为**有序**，3.6中无法100%确定有序，3.6之前是无序的。**其长度大小可变，元素可任意删减和改变**。

与元组和列表相比，字典性能更优，对于查找、添加、删除操作，都能在常数时间复杂度内完成。

集合：集合和字典基本相同，区别：集合没有键和值的配对，是一系列无序的、唯一的（不重复）元素组合。

**字典和集合的创建**

```python
#创建字典
d1 = {'name':'jason','age':20,'gender':'male'}
d2 = dict({'name':'jason','age':20,'gender':'male'})
d3 = dict([('name','jason'),('age',20),('gender','male')])
d4 = dict(name='jason',age=20,gender='male')
print(d1 == d2 ==d3 ==d4)	#True

#创建集合
s1 = {1,2,3,4}
s2 = set([1,2,3,4])
print(s1 == s2)		#True

#字典和集合中，无论键和值都可以是混合类型。
s = {1,'hello',5.0}

元素访问，字典访问可以直接索引键，不存在就会抛出异常，也可以通过使用get(key,default)函数来进行索引，若键不存在，调用get()函数可以返回一个默认值。default没有指定时，默认为None：

d1 = {'name':'jason','age':20,'gender':'male'}
d2 = dict({'name':'jason','age':20,'gender':'male'})
d3 = dict([('name','jason'),('age',20),('gender','male')])
d4 = dict(name='jason',age=20,gender='male')
print(d1 == d2 ==d3 ==d4)
print(d1['name'])
print(d1['location'])

Traceback (most recent call last):
  File "D:/python_project/jike/list_tuple.py", line 8, in <module>
    print(d1['location'])
KeyError: 'location'
True
jason

集合不支持索引操作，集合本质上是一个哈希表，和列表不一样。
```

判断一个元素在不在字典/集合中，可以使用**value in dict/set**来判断。

```python
#创建字典
d1 = {'name':'jason','age':20,'gender':'male'}
print('name' in d1) #判断键
print('jason' in d1)
#创建集合
s1 = {1,2,3,4}
print(1 in s1)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
True
False
True

Process finished with exit code 0
```

**字典和集合的增、删和更新操作**

```python
#创建字典
d1 = {'name':'jason','age':20,'gender':'male'}
d1['dob'] = '1999-02-01'    #增加元素对：'dob':'1999-02-01'
print(d1)
print(d1.pop('dob'))   #删除d1中键为'dob'的元素对
print(d1)
#创建集合
s1 = {1,2,3,4}
s1.add(5)   #增加元素5到集合
print(s1)
s1.remove(5)    #从集合中删除元素5，集合的pop()操作删除集合中的最后一个元素，由于集合本身是无序的，慎用pop()
print(s1)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
{'name': 'jason', 'age': 20, 'gender': 'male', 'dob': '1999-02-01'}
1999-02-01
{'name': 'jason', 'age': 20, 'gender': 'male'}
{1, 2, 3, 4, 5}
{1, 2, 3, 4}

Process finished with exit code 0
```

**字典和集合的排序**

```python
#创建字典
d1 = {'a':30,'b':10,'c':20}
#根据字典键升序排列,返回列表
d1_sorted_bykey = sorted(d1.items(),key=lambda x:x[0])
#根据字典值升序排列，返回列表
d1_sorted_byvalue = sorted(d1.items(),key=lambda x:x[1])
print(d1_sorted_bykey)
print(d1_sorted_byvalue)
#创建集合
s1 = {1,3,2,4}
sorted(s1) #升序排序
print(sorted(s1))   #返回排序后的列表
print(s1)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
[('a', 30), ('b', 10), ('c', 20)]
[('b', 10), ('c', 20), ('a', 30)]
[1, 2, 3, 4]
{1, 2, 3, 4}

Process finished with exit code 0
```

**思考题**

```python
1.
d1 = {'a':1,'b':2,'c':3}	#{}是关键字，直接调用底层c代码，效率高
d2 = dict({'a':1,'b':2,'c':3})	#函数，效率低
2.列表不可以做字典的键，因为列表是可变的。key是要求不可变的
```

## 03 字符串（string）

### 字符串基础

字符串：由独立字符组成的一个序列，通常包含在单引号(' ')、双引号(" ")和三引号('''  ''')或("""   """)之中。

这样便于在字符串中内嵌带引号的字符。

python也支持转义字符

```python
常见的转义字符
\newline		接下一行
\\				表示\
\'				表示单引号'
\"				表示双引号"
\n				换行
\t				横向制表符
\b				退格
\v				纵向制表符
```

```python
s = 'a\nb\tc'
print(s)
print(len(s))

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
a
b	c
5

Process finished with exit code 0
```

### **字符串常用操作**

```python
s = 'jason'
#索引
print(s[0])
#切片,[index1:index2]表示第index1到index2 - 1个元素组成的子字符串
s1 = s[1:3]
print(s1)
print(len(s))
#遍历字符串
for c in s:
    print(c)
#修改字符串，因为字符串不可变，所以通常只能通过创建新字符串来完成

#s = 'J' + s[1:]    #'H'和原字符串切片拼接
s = s.replace('j','J')  #扫瞄原字符串替换
print(s)

#字符串拼接
str = 'ab'
str1 = 'cd'
str += str1     #str没有其它引用时，会尝试在原地扩充字符串大小，不会重新分配内存来创建新字符串进行拷贝
str2 = ' '.join('abcd') #按照指定格式将每个元素拼接起来
print(str)
print(str2)

D:\Enviroments\python\python\python3.exe D:/python_project/jike/list_tuple.py
j
as
5
j
a
s
o
n
Jason
abcd
a b c d

Process finished with exit code 0
常见函数：
string.strip(str)，表示去掉首尾的str字符
string.lstrip(str)，表示只去掉开头的str字符
string.rstrip(str)，表示只去掉尾部的str字符
```

### 字符串的格式化

**格式化函数**

```python
1、print('no data available for person with id:{},name:{}'.format(id,name))
	
    string.format()-格式化函数
	{}-格式符，为后来的真实值预留位置
    
2、print('no data available for person with id:%s,name:%s'.%(id,name))
```



