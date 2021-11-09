---
title: python高阶
type: "_posts"
layout: "posts"
img: "https://raw.githubusercontent.com/longbig/hexo-blogs/master/source/img/01.jpeg"
---
# python高阶

## 面向对象

### 基本概念

#### 类（class）

描述具有相同属性和行为的对象的集合，如：学生类（学号，姓名，班级，学习）

#### 对象（object）

通过类定义的数据结构的实例，是对类的具体实现

##### 属性：描述类的静态特征

##### 类属性

每一个对象都具有，并且值相同，如：学生的国籍

##### 实例属性

每一个对象都具有，但值可能不同，如：学生姓名、年龄等

方法：描述类的动态行为

##### 类方法

通过装饰器\@classmethod声明，通常通过类调用，一般用于修改类属性的值

##### 实例方法

类中最常用的方法，常通过对象调用

##### 静态方法

通过装饰器\@staticmethod声明，常通过类调用，通常是一些和类本身无关的方法

##### 类的声明

**语法**

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/1.jpg?raw=true){width="4.166666666666667in" height="1.5074529746281715in"}

**类名**：符合标识符命名规范，通常每个单词首字母大写

例1：声明一个学生类

**属性**：学号、姓名、年龄、国籍、班级

**方法**：学习、吃饭、睡觉

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/2.jpg?raw=true){width="4.166666666666667in" height="2.3263353018372706in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/3.jpg?raw=true){width="4.166666666666667in" height="3.659326334208224in"}

##### 对象的声明（实例化）

语法：对象名 = 类名(\[实参1，实参2，\...\...\])

例1：实例化Student类

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/4.jpg?raw=true){width="4.166666666666667in" height="2.542010061242345in"}

##### 内置方法（重要）

\_\_new\_\_()，new方法，在实例化是自动调用，用于创建对象

\_\_init\_\_()，构造方法，初始化对象，在实例化时自动调用

\_\_del\_\_()，析构方法，销毁对象，在对象生命周期结束时自动调用

例1：顺序：创建\-\--》构造\-\-\--》销毁

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/5.jpg?raw=true){width="4.166666666666667in" height="3.444122922134733in"}

例2：

声明一个学校类，学校类中声明一个类属性表示学校的总人数，声明一个类方法用于更新学校总人数

声明一个学生类，包含学生的基本信息，每实例化一个学生，则学校的总人数+1

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/6.jpg?raw=true){width="4.166666666666667in" height="2.4410772090988626in"}

例3：

声明一个学校类，学校类中声明4个类属性分别表示学校的总人数、高一、高二、高三年级的人数，声明一个类方法用于更新学校总人数以及对应年级的人数

声明一个学生类，包含学生的基本信息，每实例化一个学生，则学校的总人数+1

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/7.jpg?raw=true){width="4.166666666666667in" height="2.312234251968504in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/8.jpg?raw=true){width="4.166666666666667in" height="1.6754461942257217in"}

##### 对象组合

用于描述类与类之间的关系，多个类之间存在依赖关系，需要在A类中调用B的属性或者方法

**方式**

1、在A类的实例方法中传入B类的对象，通过该对象调用B类中的属性和方法（A类、B类相互依赖）

2、在A类的构造方法中传入B类的对象，通过该对象调用B类中的属性和方法（A类依赖于B类）

例1：饲养员与动物

有10个房间，每个房间中随机放入老虎或羊

饲养员不知道每个房间中的动物类型，可以选择敲门（房间中的动物发出叫声，同时体重-5）获知动物类型。饲养员给动物喂食，喂正确则体重+10，错误则体重-10（老虎吃肉，羊吃草）

游戏时间1分钟，统计每个房间中动物的体重

分析：完成整个事件有哪些对象，这些对象具有哪些属性和方法，将对象的属性和方法抽象为类

老虎

属性：名字、体重

方法：吃东西、发出叫声

羊

属性：名字、体重

方法：吃东西、发出叫声

房间

属性：房间号、动物类型

饲养员

属性：姓名

方法:敲门、喂食

代码实现

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/9.jpg?raw=true){width="4.166666666666667in" height="3.3277088801399826in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/10.jpg?raw=true){width="4.166666666666667in" height="3.031418416447944in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/11.jpg?raw=true){width="4.166666666666667in" height="2.1454385389326336in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/12.jpg?raw=true){width="4.166666666666667in" height="2.448050087489064in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/13.jpg?raw=true){width="4.166666666666667in" height="1.9184426946631672in"}

### 面向对象的三大特性

#### 封装

私有化：在属性或者方法名前面加2条下划线，此时属性或方法就变为私有的，只能在当前类的内部访问，在类的外部无法直接访问私有属性或者方法

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/14.jpg?raw=true){width="4.166666666666667in" height="1.700269028871391in"}

#### 继承

作用：提高代码重用性，降低代码冗余

基本概念：

子类：继承其它类的类

可以有多个父类

可以继承父类所有非私有的属性和方法

父类：也叫基类、超类，被别的类来继承的类

重写：子类继承父类的方法，在子类中重新实现该方法

例1：

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/15.jpg?raw=true){width="4.166666666666667in" height="3.9289107611548557in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/16.jpg?raw=true){width="4.166666666666667in" height="1.063218503937008in"}

例2：父类控制子类必须重写方法

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/17.jpg?raw=true){width="4.166666666666667in" height="2.6574234470691165in"}

例3：单例模式

在程序运行期间保证类的实例只有1个

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/18.jpg?raw=true){width="4.166666666666667in" height="2.1680686789151355in"}

#### 多态

作用：增加代码的灵活性、可扩展性

例

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/19.jpg?raw=true){width="3.8541666666666665in" height="4.165555555555556in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/20.jpg?raw=true){width="4.166666666666667in" height="0.8117399387576553in"}

### 多线程

作用：提高代码的执行速度

线程：进程内部进行CPU调度的基本单位，一个进程至少存在一个线程

模块：threading

创建线程：Thread(target=func\[args=(value1,value2,\...\...)\])

target，指定线程需要执行的任务（通常是函数名或者方法名，不要加括号）

args，指定线程执行的任务需要传入的实参，以元组形式传入

启动线程：start()

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/21.jpg?raw=true){width="4.166666666666667in" height="3.2630522747156605in"}

##### 线程守护

作用：子线程跟随主线程结束而结束

方法：setDaemon(True)，必须在线程启动前设置

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/22.jpg?raw=true){width="4.166666666666667in" height="3.4368832020997377in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/23.jpg?raw=true){width="4.166666666666667in" height="2.677891513560805in"}

##### 线程阻塞

作用：主线程在子线程结束之后再结束

方法：join()，需要在线程启动后设置

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/24.jpg?raw=true){width="4.166666666666667in" height="2.583507217847769in"}

##### 线程锁

作用：用于解决子线程共享全局变量时出现的数据冲突问题，从而确保数据的安全性和准确性

缺点：降低程序运行效率

使用步骤：

导入模块：Lock

1、创建锁：lock = Lock()

2、在编辑全局变量之前获取锁，锁定全局变量只能由当前子线程编辑

lock.acquire()

3、编辑完成后，释放锁（一定记得释放）

lock.release()

未加锁

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/25.jpg?raw=true){width="4.166666666666667in" height="4.002409230096238in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/26.jpg?raw=true){width="4.166666666666667in" height="0.7414271653543307in"}

添加锁

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/27.jpg?raw=true){width="4.166666666666667in" height="3.855485564304462in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/28.jpg?raw=true){width="4.166666666666667in" height="2.603734689413823in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/29.jpg?raw=true){width="4.166666666666667in" height="3.663277559055118in"}

### 正则表达式

作用：实现对字符串的复杂控制

模块：re（系统模块）

方法：

split(pattern,string)，使用字符串中与pattern规则匹配的内容进行分隔，返回一个列表

pattern，正则表达式

string，待处理的字符串

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/30.jpg?raw=true){width="4.166666666666667in" height="2.2630227471566053in"}

sub(pattern,repl,string)，将字符串中与pattern规则匹配的内容进行替换（替换成repl），返回一个新字符串

pattern，正则表达式

string，待处理的字符串

repl，新内容

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/31.jpg?raw=true){width="4.166666666666667in" height="2.40252624671916in"}

findall(pattern，string\[，控制字符串\])：以列表返回字符串中与pattern规则匹配的内容，如果没有匹配的则返回空列表

pattern，正则表达式

string，待处理的字符串

#### 控制字符

re.S，使用元字符.可以匹配包括换行符\\n在内的所有字符

re.I，忽略大小写

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/32.jpg?raw=true){width="4.166666666666667in" height="2.2089687226596677in"}

#### 元字符

\\w，匹配一个单词字符（字母、数字、下划线）

\\W，匹配一个非单词字符

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/33.jpg?raw=true){width="4.166666666666667in" height="2.92294072615923in"}

\\d，匹配一个数字字符

\\D，匹配一个非数字字符

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/34.jpg?raw=true){width="4.166666666666667in" height="2.85534886264217in"}

\\s,匹配一个空白字符

\\S，匹配一个非空白字符

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/35.jpg?raw=true){width="4.166666666666667in" height="2.90325021872266in"}

**.**，匹配除换行符\\n以外的任意一个字符

**\^**，匹配字符串开头

**\$**，匹配字符串结尾

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/36.jpg?raw=true){width="4.166666666666667in" height="2.8333333333333335in"}

\*,匹配前一个字符任意次

ab\*\--a、ab、abb、abbb

+，匹配前一个字符至少1次

？，匹配前一个字符0次或1次

{n}，匹配前一个字符n次

{n，}，匹配前一个字符至少n次

{n,m}，匹配前一个字符至少n次，最多m次

{，m}，匹配前一个字符最多m次

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/37.jpg?raw=true){width="4.041666666666667in" height="4.158301618547681in"}

### 网络编程-TCP/IP简介

OSI模型

TCP/IP模型（当今互联网网络模型）

应用层：HTTP、HTTPS、FTP（文件传输协议）、SMTP、IMAP、POP3

HTTP协议请求方法（最常用）：GET、POST

传输层：TCP、UDP

UDP，用户数据报协议，提供无连接、不可靠的通信服务（效率高、消耗少）

TCP，传输控制协议，提供面向连接、可靠的通信服务（安全性、可靠性高）

三次握手

建立连接

四次挥手

断开连接

socket编程

套接字，工作在传输层和应用层之间，通过TCP或UDP协议传输信息，分为客户端和服务端

模块，socket

使用步骤

服务端

1、创建socket对象：soc = socket.socket()

2、绑定IP端口：soc.bind(ip,port)

3、设置监听：soc.listen()

4、等待客户端连接：soc.accept()

客户端

1、创建socket对象：soc = socket.socket()

2、连接服务器：soc.connect(ip,port)

公共方法：

send()，发送消息

recv()，接收消息

例：

服务端

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/38.jpg?raw=true){width="4.166666666666667in" height="2.345429790026247in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/39.jpg?raw=true){width="4.166666666666667in" height="2.0285454943132106in"}

客户端

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/40.jpg?raw=true){width="4.166666666666667in" height="2.0153827646544182in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/41.jpg?raw=true){width="4.166666666666667in" height="0.9444444444444444in"}

request

作用：模拟客户端向服务端发送http或https请求

模块：requests

pip install requests

GET请求：

get(url\[,params,headers,file\])

url，请求地址

params，请求参数，一般使用字典传入

headers，请求头

file，一般用于上传文件

例1：获取豆瓣电影排行榜

1、抓包，获取请求地址、参数、请求头

2、使用代码模拟客户端发送请求，获取页面源码

3、使用正则表达式从页面源码中获取排行榜中的电影信息

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/42.jpg?raw=true){width="4.166666666666667in" height="1.580155293088364in"}

例2：下载网页图片

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/43.jpg?raw=true){width="4.166666666666667in" height="1.7040343394575679in"}

## 高阶应用

### 装饰器

#### 闭包函数

定义：外函数中声明了一个内函数，在内函数中引用了外函数的变量，外函数返回内函数的引用

例1：

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/44.jpg?raw=true){width="4.166666666666667in" height="2.2631135170603676in"}

例2：

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/45.jpg?raw=true){width="4.166666666666667in" height="2.555858486439195in"}

例3：内函数中修改外函数变量

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/46.jpg?raw=true){width="4.166666666666667in" height="2.270722878390201in"}

### 装饰器

在不改变函数的源码、调用方式的前提下，为函数添加新的功能

通用装饰器模板：

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/47.jpg?raw=true){width="4.166666666666667in" height="1.5924956255468066in"}

例1：统计函数的运行时间

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/48.jpg?raw=true){width="4.166666666666667in" height="2.5290365266841643in"}

例2:执行顺序

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/49.jpg?raw=true){width="4.166666666666667in" height="2.483672353455818in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/50.jpg?raw=true){width="4.166666666666667in" height="1.2755107174103237in"}

例3：为装饰器传参（三层的装饰器能够实现为装饰器传参）

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/51.jpg?raw=true){width="4.166666666666667in" height="2.5325699912510937in"}

## pytest框架

模块：pytest

pip insatll pytest

### 基本使用方法

说明：

函数名需要以test开头

类名需要以Test开头，类中的方法需要以test开头

类中不能有构造方法（初始化对象）

使用assert进行断言

脚本名需要以test开头

#### 作用于函数

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/52.jpg?raw=true){width="4.166666666666667in" height="1.6981506999125109in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/53.jpg?raw=true){width="4.166666666666667in" height="1.8821839457567804in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/54.jpg?raw=true){width="4.166666666666667in" height="0.8638637357830271in"}

#### 作用于类

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/55.jpg?raw=true){width="4.166666666666667in" height="1.7446237970253717in"}

##### 用例执行

方式

脚本：pytest.main(\[参数1，参数2，\...\...\])

命令行

pytest 参数 脚本

py.test 参数 脚本

python -m pytest 参数 脚本

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/56.jpg?raw=true){width="4.166666666666667in" height="1.8027449693788276in"}

##### 参数

-s

-v

-q

-k，通过关键字匹配脚本、函数名、类名、方法名

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/57.jpg?raw=true){width="4.166666666666667in" height="2.1729385389326334in"}

-x，如果测试执行过程中有fail的用例，则测试立即停止

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/58.jpg?raw=true){width="4.166666666666667in" height="2.1729385389326334in"}

\--maxfail=n，当失败用例达到n条则停止测试

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/59.jpg?raw=true){width="4.166666666666667in" height="2.1729385389326334in"}

-m，对用例进行标记，执行指定的用例

1、在项目根目录下新建文件pytest.ini

2、在pytest.ini文件中添加标记

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/60.jpg?raw=true){width="4.166666666666667in" height="2.8889971566054244in"}

3、使用装饰器标记测试用例\@pytest.mark.标记

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/61.jpg?raw=true){width="4.166666666666667in" height="1.855275590551181in"}

4、执行测试时使用-m 标记即可执行指定的用例

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/62.jpg?raw=true){width="4.166666666666667in" height="1.7165102799650043in"}

##### 跳过用例

\@pytest .mark.skip(reason=xxxx)，无条件跳过指定用例

\@pytest mark.skipif(条件，reason=xxxx)，有条件跳过指定用例

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/63.jpg?raw=true){width="4.166666666666667in" height="2.893416447944007in"}

##### 参数化

\@pytest .mark.parametrize(\'参数1，参数2，\...\...\'，值)

参数，与被装饰的函数的形参相同

值，传递给参数的数据，通常为一个列表，如果需要给多个参数传数据可以将这些数据封包到元组中

例1：一个参数情况

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/64.jpg?raw=true){width="4.166666666666667in" height="1.4433300524934383in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/65.jpg?raw=true){width="4.166666666666667in" height="1.9778094925634295in"}

例2：多个参数（每条用例的数据封包到元组中）

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/66.jpg?raw=true){width="4.166666666666667in" height="1.4064020122484688in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/67.jpg?raw=true){width="4.166666666666667in" height="1.5560269028871392in"}

例3：登录测试用例

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/68.jpg?raw=true){width="4.166666666666667in" height="2.147295494313211in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/69.jpg?raw=true){width="4.166666666666667in" height="1.432571084864392in"}

##### 前置后置

模块级，作用范围为当前模块，模块中的所有用例执行前后分别执行1次前置和后置

setup_module()，前置，所有用例执行前运行1次

teardown_module()，后置，所有用例执行后执行1次

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/70.jpg?raw=true){width="4.166666666666667in" height="3.3808234908136483in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/71.jpg?raw=true){width="4.166666666666667in" height="2.718675634295713in"}

函数级，作用范围为当前模块中的每一个测试函数，模块中的每条用例执行前后分别运行1次前置和后置

setup_function()，前置，每条用例执行前运行1次

teardown_function()，后置，每条用例执行后运行1次

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/72.jpg?raw=true){width="4.166666666666667in" height="3.1950885826771653in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/73.jpg?raw=true){width="4.166666666666667in" height="3.486307961504812in"}

类级，作用范围为当前类，类中的所有用例执行前后分别运行1次前置和后置

setup_class()，前置，所有用例执行前运行1次

teardown_class()，后置，所有用例执行后运行1次

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/74.jpg?raw=true){width="4.166666666666667in" height="2.65544072615923in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/75.jpg?raw=true){width="4.166666666666667in" height="2.337912292213473in"}

方法级，作用范围为当前类中的每一个测试方法，每条用例执行前后分别运行1次前置和后置

setup_method()或者setup()，前置，每条用例执行前运行1次

teardown_method()或者teardown()，后置，每条用例执行后运行1次

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/76.jpg?raw=true){width="4.166666666666667in" height="3.407755905511811in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/77.jpg?raw=true){width="4.166666666666667in" height="2.5226760717410324in"}

用例：新增会员

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/78.jpg?raw=true){width="4.166666666666667in" height="2.254727690288714in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/79.jpg?raw=true){width="4.166666666666667in" height="1.4150393700787403in"}

##### fixture

创建：\@pytest .fixture(\[name,scope,params,autouse\])

name，用于指定fixture名称，如果不指定默认为被装饰的函数名

scope，指定固件fixture作用范围，module,class,function(默认),session,package

params，参数

autouse,设置为True，实现自动调用fixture

例1：局部fixture

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/80.jpg?raw=true){width="4.166666666666667in" height="2.110239501312336in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/81.jpg?raw=true){width="4.166666666666667in" height="2.270722878390201in"}

通过yield实现后置

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/82.jpg?raw=true){width="4.166666666666667in" height="2.802257217847769in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/83.jpg?raw=true){width="4.166666666666667in" height="1.7833891076115485in"}

##### 全局fixture

1、在项目下创建conftest.py文件，在该文件中实现fixture

可在所有的脚本中使用该fixture（yeild返回一个值）

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/84.jpg?raw=true){width="4.166666666666667in" height="1.8820220909886265in"}

2、调用

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/85.jpg?raw=true){width="4.166666666666667in" height="1.6881255468066492in"}

执行结果

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python2/86.jpg?raw=true){width="4.166666666666667in" height="1.9246030183727034in"}

