---
title: python面向对象（一）
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

