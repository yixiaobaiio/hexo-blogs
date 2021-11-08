# Python基础

## 标识符，变量名、函数名、类名统称

### 命名规范

​	只能包含字母、数字、下划线，并且不能以数字开头

​	不能与系统关键字、模块名相同

​	系统关键字

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/1.jpg?raw=true)

​	严格区分大小写

​	尽量使用有意义的英文单词

​		a = 20（无意义）

​		age = 20

​	多个单词之间使用下划线连接

​		student_age = 20

### 变量

​	声明：取个名字，给一个值（必须赋值；运算符左右两边加空格，提高代码可读性）

​		var = \'abc\'

​		var = 100

​		var = 100.98

​		var = True

### 输入输出

​	输入：input(\[\'message\'\])

​		接收外部输入，无论输入哪种数据类型的值，都统一作为字符串处理

​		代码遇到input函数会暂停，直到敲入回车键后代码继续运行

​		message为可选的参数，一般用于输入的提示

​	输出：print(value1,value2,\...\...sep=\' \',end=\'\\n\',file=sys.stdout)

​		value1,表示要输出的内容，可以同时输出多个对象，中间使用逗号隔开

​		sep，在结果中多个对象值的分隔符，默认为空格

​		end，表示输出完成后的结束符，默认为换行符（\\n）

​		file，将内容输出到指定文件

​		例1

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/2.jpg?raw=true)

### 数据类型

​		type(obj)，返回对象的类型

​		布尔型：bool

​		声明后不能改变

​		只有两个值：True、False

​		0、None、空字符、空列表、空字典，返回False，其他返回True

​	整型：

​		int（整数）

​		声明后不能被改变

​	浮点型：

​		float（带小数）

​		声明后不能被改变

​	字符串：

​		str，包含在引号之间的内容（可以是单引号、双引号、三引号）

​		声明后不能被改变

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/3.jpg?raw=true)

​	元组：

​		tuple，包含在()之间的内容，每一个元素之间使用逗号分隔，元组中的元素可以是任意数据类型

​		声明：tup = (1,2,3,4)

​		声明后不能被改变

​	列表：

​		list，包含在\[\]之间的内容，每一个元素之间用逗号分隔，列表中的元素可以是任意数据类型

​		li = \[1,2,1.2,\'abcd\',True,\[1,2,3\]\]

​	字典：

​		dict，包含在{}之间的内容，每一个元素为一个键值对（key:value）,键只能为不可变的数据类型（int、				float、布尔型、字符串、元组），值可以为任意数据类型

​		声明：dic = {\'name\':\'lucy\',1:\[1,2,3\],1.8:{},True:\'abc\',(1,2):1000}

​	集合（不常用）：

​		set，包括在{}之间的内容，每一个元素之间使用逗号分隔，集合中的元素可以是任意数据类型

​		集合中的元素不会重复，常用集合来去重

​	数据类型转换

​		bool（obj），根据对象的值返回布尔值

​		0、None、空字符、空列表、空字典、空元组，返回False

​		int（obj），将对象转换为整型

​	布尔型\-\-\-\-\--\>整型

​		True \-\-\-\-\--\> 1

​		False \-\-\-\-\--\> 0

​	浮点型\-\-\-\-\--\>整型

​		做截取（取整），会损失精度

​		字符串\-\-\-\-\--\>整型

​		字符串中不能包含任何非数字字符

​		float(obj)，将对象转换为浮点型

​	布尔型\-\-\-\-\--\>浮点型

​		True \-\-\-\-\--\> 1.0

​		False \-\-\-\-\--\> 0.0

​	整型\-\-\-\-\--\>浮点型

​	字符串\-\-\-\-\--\>浮点型

​	字符串中不能包含小数点以外的任何非数字字符

​	tuple(obj)，将对象转换为元组

​		字符串\-\-\-\-\--\>元组

​		列表\-\-\-\-\--\>元组

​		字典\-\-\-\-\--\>元组

​	元组中只有键

​	list(obj)，将对象转换成列表

​		字符串\-\-\-\-\--\>列表

​		元组\-\-\-\-\--\>列表

​		字典\-\-\-\-\--\>列表

​	列表中只有键

​	集合\-\-\-\-\--\>列表

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/4.jpg?raw=true)

### 格式化

​	占位符

​	语法：%\[-w.p\]type

​		-，表示左对齐，默认是右对齐

​		w，表示宽度

​		p，表示精度

​		type，表示数据类型（d-整数，f-浮点数，s-字符串）

​	例1：

​		%5.2f，表示一个浮点数，宽度为5，精确到小数点后第2位

​		%-5s，表示一个字符串，宽度为5，左对齐

​	例2：

​		输入一个用户的姓名手机号，按以下格式输出：姓名\--xxx；手机号\--xxxxxxxxxxx

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/5.jpg?raw=true)

​	例3：

​		输入学生的姓名、成绩，按格式输出每个学生的成绩信息、平均成绩（保留2位小数）

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/6.jpg?raw=true)

format

语法：\' \'{:w.p}\'.format(var) \'

​	默认左对齐

​	w，宽度

​	pf，表示浮点数的精度

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/7.jpg?raw=true)

f-string

语法：f\'{var\[:w.pf\]}\'

​	w，宽度

​	pf，表示浮点数的精度

​	例：

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/8.jpg?raw=true)

### 运算符

#### 算术运算符

+，加法，返回两个对象的和

如何两个对象是字符串，则做字符串拼接

\'abc\' + \'efg\' = \'abcefg\'

-，减法，返回两个对象的差

\*，乘法，返回两个对象乘积

如果运算的对象为1个字符串，1个数字，则复制该字符串n次，如：\'a\' \* 5 = \'aaaaa\'

/，除法，返回两个对象的商

//，整除，返回小于等于两个对象商的最大整数

5 // 2 = 2

5 // -2 = -3

\*\*，幂运算

3 \*\* 2 = 9

10 \*\* 2 = 100

10 \*\* -2 = 0.01

%，返回两个对象相除的余数

公式：r = a % b = a - b \* (a // b)

5 % -2 = -1

-5 % 2 = 1

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/9.jpg?raw=true)

#### 赋值运算符

=

+=

-=

\*=

/=

//=

\*\*=

%=

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/10.jpg?raw=true)

#### 比较运算符

运算结果为布尔值：True、False

== ，比较两个对象的值是否相等

\>、>=、\<、\<=、!=

字符串可以比较，比较的是ascii码

#### 逻辑运算符

运算对象为布尔表达式，运算结果为布尔值

and，参与运算的对象结果都为True，整体表达式结果为True，否则为False

or，参与运算的对象只要任意一个结果为True，整体表达式结果为True，都为False，结果为False

not，参与运算的对象结果为True，整体结果则为False，参与运算的对象结果为False，整体结果则为True

## 数据结构

### 通用方法

len(obj),返回对象（字符串、列表、元组、字典、集合）中的元素个数

sum(obj)，返回对象（列表、元组、字典、集合）中所有元素的和

max(obj)，返回对象（列表、元组、字典、集合、字符串）中最大元素

zip(obj1，obj2，\...\...)，将多个对象打包

### 字符串方法

语法：字符串.方法名（\[参数\]）

count(sub\[,start\[,end\]\])，返回字符串中指定范围内指定子字符串的数量

sub，表示待查找的子字符串

start，表示开始位置索引

end，表示结束位置索引

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/11.jpg?raw=true)

index(sub\[,start\[,end\]\])，返回子字符串在字符串中的索引

如果有多个相同的子字符串则返回第一个的索引

如果不存在指定的子字符串，则报错

upper()，将字符串转换成大写

lower()，将字符串转换成小写

title()，将单词的首字母转换成大写

startswith(sub)，检查是否以指定的子字符串开始，如果是返回True，否则返回False

endswith(sub)，检查是否以指定的子字符串结尾，如果是返回True，否则返回False

replace(old,new\[,count\])，替换，可以指定替换次数（默认全部替换）

strip()，去除字符串前后的空字符

split(\[char\])，将字符串使用指定的字符（如果不指定则默认使用空字符）分割，返回一个列表（字符串\-\--\>列表）

join(iterable)，将可迭代对象转换为字符串,数字不可使用

rjust(len,c)：右填充

center(len,c)：中间填充

ljust(len,c)：左填充

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/12.jpg?raw=true)

len，填充后字符串的长度

c，填充的字符

isdecimal():判断字符串是否由数字组成，如果是返回True，否则返回False

isdigit()：判断字符串是否由数字组成，如果是返回True，否则返回False

isnumeric()：判断字符串是否由数字组成，如果是返回True，否则返回False

isalpha()：判断字符串是否由字母组成，如果是返回True，否则返回False

isalnum()：判断字符串是否由字母或者数字组成，如果是返回True，否则返回False

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/13.jpg?raw=true)

### 元组方法

元组特点：声明后不可变

语法：元组名.方法名(\[参数\])

index(obj)：返回指定元素在元组中的索引，指定元素不存在则报错

count(obj)：返回指定元素在元组中的数量，指定元素不存在返回0

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/14.jpg?raw=true)

### 列表方法（修改列表）

语法：列表.方法名(\[参数\])

index(obj)：返回指定元素在列表中的索引，指定元素不存在则报错

count(obj)：返回指定元素在列表中的数量，指定元素不存在返回0

clear()：清空列表元素

remove(obj)：删除列表中指定的元素

如果不存在报错

如果存在多个相同元素，则删除索引最小的

pop(\[index\])，根据索引删除列表元素（如果不指定索引则删除最后一个元素）

append(\[obj\])，在列表末尾添加元素，可以是任何类型的元素

insert(index,obj)，在列表指定索引位置插入元素

extend(iterable)，将一个可迭代对象的元素分别添加到列表

![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/15.jpg?raw=true)

区别：

append()和insert()将元素作为整体添加

extend()将元素拆开添加到列表

sort(\[reverse = True\[,key = obj\]\]),排序，默认为升序

reverse = True，表示降序排列

key，指定用于排序的值

reverse()，将列表反向

copy()，复制列表值

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/16.jpg?raw=true)

### 字典方法

语法：字典.方法名(\[参数\])

pop(key)，删除指定的键

get(key)，返回指定键的值，如果键不存在返回None

values()，以dict_values类型返回字典中所有的值

keys()，以dict_keys类型返回字典中所有的键

update(obj)，将指定对象更新到字典中

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/17.jpg?raw=true)
>
> setdefault(key,default_value)，返回指定键key的值，如果这个键不存在则新增键值(key:default_value)对，并且返回default_value

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/18.jpg?raw=true)

items()，元组的方式返回键值对

popitem(),删除键值对，随机删除

framkeys(),根据可迭代对象快速创建一个字典

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/19.jpg?raw=true)

### 可迭代对象

字符串、元组、字典、列表、集合

含有\_\_iter\_\_（）方法的对象就是可迭代对象

支持循环遍历（for）

序列

​	数据类型：字符串、元组、列表

​	操作类型：

索引，可以根据索引访问序列中的元素（0，len（obj）-1）

语法：obj\[index\]

切片，通过索引返回对象的子元素片段

语法：obj\[start:end:step\]

start，开始位置，如果省略表示从第一个位置开始

end，结束位置，实际返回的是end-1位置上的元素，如果省略表示取到最后一个元素

step，表示步长(每间隔多少元素取一个)，省略表示1

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/20.jpg?raw=true){width="4.166666666666667in" height="1.5923118985126858in"}

非序列

​	字典

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/21.jpg?raw=true){width="4.166666666666667in" height="0.6278543307086614in"}

​	集合

### 控制结构

#### 分支语句（if）

单分支

描述了程序在布尔表达式结果为 True的情况下需要执行的操作

语法：注意冒号和缩进（默认为4个空格）

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/22.jpg?raw=true){width="4.166666666666667in" height="1.7302263779527558in"}

例1:输出学生的成绩，成绩>=60，输出合格，否则输出不合格

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/23.jpg?raw=true){width="4.166666666666667in" height="0.8173075240594926in"}

双分支

描述了程序在布尔表达式结果为True或者False的情况下需要执行的操作

语法：

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/24.jpg?raw=true){width="4.166666666666667in" height="2.1260684601924758in"}

例2 判断奇偶数

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/25.jpg?raw=true){width="4.166666666666667in" height="0.7133147419072616in"}

多分支

描述了程序在不同的布尔表达式下分别需要进行的操作

语法：

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/26.jpg?raw=true){width="4.166666666666667in" height="3.176567147856518in"}

例3

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/27.jpg?raw=true){width="4.166666666666667in" height="1.5801891951006124in"}

嵌套if语句

例4

> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/28.jpg?raw=true){width="4.166666666666667in" height="1.4583333333333333in"}
>
> ![](https://github.com/yixiaobaiio/hexo-blogs/blob/master/source/img/python/29.jpg?raw=true){width="4.166666666666667in" height="1.197691382327209in"}

#### 循环语句（while、for）

while语句

描述了程序在指定条件成立的情况下重复完成某个操作

语法：

> ![](media/rb8jyvctlvoxdua03czor.png){width="4.166666666666667in" height="1.0919925634295713in"}

例1:输出0-9这10个数字

> ![](media/xx6dbwpj4u1nheeoct3zq.png){width="4.166666666666667in" height="0.9540496500437445in"}

例2:计算1+2+3+\...+10的和

> ![](media/t168ef86o99m7akf2xk8a.png){width="4.166666666666667in" height="0.803082895888014in"}
>
> ![](media/vtldhhnxrfos5puth0dxc.png){width="4.166666666666667in" height="1.2770428696412948in"}

例3:循环次数未知，可以通过变量值的变化控制循环继续还是结束

使用字典保存用户信息userinfo = {\'user1\':\[\'123456\',\'张三\'\],\'user2\':\[\'123456\',\'李四\'\]}，完成注册和登录功能

注册，如果用户名已经存在，提示错误；如果密码不是6位数字，提示错误

> ![](media/umzn6iox0a5321n1m7x3m.png){width="4.166666666666667in" height="1.0436286089238844in"}

for语句

适用于循环次数确定的循环

语法：

> ![](media/brk59jvxkob2788pdqt15o.png){width="4.166666666666667in" height="0.672843394575678in"}

i，变量，可以不声明，在循环内部可以直接使用该变量的值

range(start,end)，生成【start，end】范围内的数字序列

例1:输出0-9这10个数字

> ![](media/sc10ir39tiby6bq8sjfwo.png){width="4.166666666666667in" height="0.8526541994750656in"}
>
> ![](media/v61mb0rvmflba2hyyd3xs.png){width="4.166666666666667in" height="0.5731517935258092in"}

例2:输入1个正整数n，计算1+2+\...+n的和，如果n=1，和为1

> ![](media/sgpvk6rfdmw8khkxb03q.png){width="4.166666666666667in" height="1.7791294838145233in"}

例3:将字符串s=\'qw\$\^e&sASd1\*23(\'中的特殊符号去掉

> ![](media/nh2rdopzj2mbt7k5jsxhes.png){width="4.166666666666667in" height="0.5642782152230971in"}

例4:嵌套for循环，打印5行5列\*

> ![](media/rzjn73n0h1k184htjlop8w.png){width="4.166666666666667in" height="0.557244094488189in"}

例5:打印九九乘法表

> ![](media/tw8lsgbc9ekwqdchyh9hr.png){width="4.166666666666667in" height="0.5224912510936133in"}

#### 循环控制语句

continue,结束当前循环，开始下一次新的循环

break，终止循环

> ![](media/44ivkpkdmujuuxcqjksx8l.png){width="4.166666666666667in" height="0.7757294400699912in"}

## 函数（重要）

声明：

> ![](media/nj1u8gapxatzm58ifumvd.png){width="4.166666666666667in" height="1.2190682414698162in"}

函数名：必须符合标识符命名规范

参数：也叫形参，可选，可以有多个。在函数内部可以直接使用形参

返回值：可选的，可以同时返回多个值，如果没有return语句默认返回None

调用：函数名(\[参数1，参数2，\...\...\])

参数：也叫实参，根据形参传入实参

例1:无参无返回值

> ![](media/0k7kfiddt1c7mcfe64k85o.png){width="4.166666666666667in" height="0.31559930008748904in"}

例2:多个参数与多个返回值

> ![](media/q6zz4cuhioppfccmkyo84h.png){width="4.166666666666667in" height="0.7960083114610673in"}

### 参数

#### 形参

必须参数（位置参数）

要求在调用时必须严格按照形参的数量、顺序、数据类型传入实参

> ![](media/b2jr7xequo49hyfsjqw2m7.png){width="4.166666666666667in" height="0.5644094488188977in"}

默认参数

在声明函数时通过键值对（key=value）的形式指定形参的值，指定了以后在调用函数时可以不为该参数传值（此时使用默认值），如果传入则使用实际传入的值

默认参数必须放在位置参数后面

> ![](media/vv4sdtuqpdjtaa5d1lvl5i.png){width="4.166666666666667in" height="0.7123239282589676in"}

可变参数

\*args，接收若干的位置参数，将传入的值封包一个元组args中

> ![](media/p2fcswni82c648idsoax6d.png){width="4.166666666666667in" height="0.6301826334208224in"}

\*\*kwargs，接收若干的关键字参数，将传入的值封包一个字典kwargs中

> ![](media/zn5dp0ay4tioplwnsfl1p.png){width="4.166666666666667in" height="0.5736132983377078in"}

#### 实参

位置参数，根据形参的数量、顺序、数据类型传入实参

关键字参数（指定参数）

在调用函数时，通过键值对（key=value）形式指定将实参传给某个形参，此时可以不用再关心参数顺序

> ![](media/2foithb0c3b5ghbbjky25s.png){width="4.166666666666667in" height="0.7266546369203849in"}

练习

> ![](media/r410oj8tzreige6sq5517.png){width="4.166666666666667in" height="1.3433759842519686in"}

### 变量作用域

#### 局部变量

在函数内部声明的变量，只能在函数内部使用

#### 全局变量

在函数外部声明的变量，可以在函数的内部使用，也可以在函数外部使用

global

在函数内部如果需要修改全局变量（不可变数据类型），需要使用global声明变量

如果全局变量为可变数据类型，在函数内部可以任意操作该全局变量，不需要使用global声明

> ![](media/4y2lsp70vkre176jnhmoxp.png){width="4.166666666666667in" height="1.1883136482939634in"}
>
> ![](media/aj3wn8pggn9hje972dw47r.png){width="4.166666666666667in" height="0.8601881014873141in"}

### 函数递归

在函数内部return返回函数本身

注意

递归需要向已知的方向进行

递归层数一般不超过1000层

> ![](media/oa6mc9aivuckgsog4ei6h.png){width="4.166666666666667in" height="0.8414326334208224in"}
>
> ![](media/08m71ix3ej0wkm4nldah2vp.png){width="4.166666666666667in" height="0.9002055993000875in"}

### 匿名函数

应用场景：不会重复调用的函数

语法：lambda\[参数1，\...\...\]:返回值

必须，并且只能有一个返回值

> ![](media/4j2u47dlu0r50ovfmyhg2f.png){width="4.166666666666667in" height="0.8464227909011374in"}

例：排序，通过匿名函数指定用于排序的key

> ![](media/f5ta41o4mcqydvmt8lcr.png){width="4.166666666666667in" height="1.1776082677165354in"}

## 模块与包

自定义模块，py文件即为一个模块

包，存在一个**\_\_init**\_\_.py文件的目录，在包中可以有若干的模块

导入

import 模块名/包名.模块名

导入一个模块，使用时通过模块名.成员名引用模块下的指定内容

> ![](media/qcm93x44es9x3sucq8x0a.png){width="4.166666666666667in" height="0.36897747156605426in"}

from 模块名/包名 import 成员1，成员2，\...\...

> ![](media/72j7f5qott50a9swoxizupi.png){width="4.166666666666667in" height="0.8817202537182852in"}

from 模块名.包名 import \*

导入模块下的所有成员

as，可以为导入的模块或者成员取别名，使用时通过别名引用即可

> ![](media/nca46gqh37am4pdt8pu3n.png){width="4.166666666666667in" height="0.4782403762029746in"}

#### 常用模块

time

> ![](media/i68dnlokxptcatl1l38m9.png){width="4.166666666666667in" height="0.358669072615923in"}

time.time()，返回1970年1月1日到当前的秒数

time.localtime()，返回本地日期信息

time.sleep()，暂停指定时间

time.strftime(\'%Y-%m-%d %X\')，返回格式化后的日期时间

%Y - 4位年；%m - 2位月；%d - 2位天

%X - 小时：分钟：秒

%H - 小时；%M - 分钟；%S - 秒

sys

sys.path，以列表返回python系统的环境变量

> ![](media/9xn3lcobg4af9nyuvrfk3f.png){width="4.166666666666667in" height="0.38777340332458443in"}

os

os.system(命令)，执行系统命令

os.getcwd()，获取当前工作命令

os.mkdir(path),创建目录

os.listdir(path)，以列表返回指定目录下的文件名、目录名

os.path.exists(path)，检查指定对象是否存在，存在返回True，否则返回False

os.path.isdir(path)，检查指定对象是否是目录，是返回True,否则返回False

os.path.isfile(path)，检查指定对象是否是文件，是返回True,否则返回False

os.path.abspath(path)，返回指定对象的绝对路径

os.path.abspath(**\_\_file\_\_**)，返回当前文件的绝对路径

os.path.dirname(**\_\_file\_\_**)，返回当前文件所在目录名称

os.path.join(path1,path2)，将两个对象拼接成一个路径

> ![](media/iqmk231zaires3fsm6f7.png){width="4.166666666666667in" height="1.6807261592300962in"}

例1:输入1个目录路径，统计出该目录下有多少个文件和目录

> ![](media/ut698ea675b6k8pcpq0e6.png){width="4.166666666666667in" height="1.4678433945756781in"}

安装第三方模块

pycharm安装：Preferences\-\--\>Project Interpreter\-\-\--\>\"+\"\-\-\--\>搜索要安装的包

命令方式（推荐）:

pip -V，返回版本

pip list，列出已经安装的所有模块

pip show 模块名，列出已经安装的指定模块的信息

pip install 模块名，从默认镜像源安装指定模块

临时配置：-i 镜像源

pip install xlrd -i 镜像源

永久配置：pip config set global.index-url 镜像源

pip config set global.index-url 镜像源

pip install xlrd

pip uninstall 模块名，卸载已经安装的模块

## 文件操作

### excel

模块:xlrd（读）

pip install xlrd

使用步骤

1、打开文件

open_workbook(path)，打开excel文件，返回一个文件对象

2、获取文件中的sheet名称

sheets（），返回excel文件中所有的sheet对象，通过对象调用name返回sheet名称

sheet_names()，返回excel文件中所有的sheet名称

sheet_by_name(sheet_name)，通过sheet名称获取指定的表

sheet_by_index(index)，通过索引获取指定的表

3、通过sheet名称获取指定表中的数据

行

nrows，返回sheet中的行数

row_values(row)，获取指定行中的数据，参数row为行号

列

ncols，返回sheet中的列数

col_values(col)，获取指定列中的数据，参数col为列号

单元格

cell_values(row,col)，返回指定单元格的数据

例

> ![](media/ql65yg464kjaagi20ttsr.png){width="4.166666666666667in" height="2.912706692913386in"}
>
> ![](media/81yieg3h1axet5ocngbe0b.png){width="4.166666666666667in" height="0.9751771653543307in"}
>
> ![](media/8z5ig6fslpxkbguyooe16g.png){width="4.166666666666667in" height="1.229942038495188in"}
>
> ![](media/2upww8a15ztpjyqz7kdo5l.png){width="4.166666666666667in" height="3.0560520559930007in"}
>
> ![](media/kq2zt6i0tlzksqqzqs0u.png){width="4.166666666666667in" height="2.922001312335958in"}

### csv

模块：csv

使用步骤：

打开文件（open）

读取文件内容（csv.reader()）

> ![](media/jkuav60g67jcaqp6ywn2b.png){width="4.166666666666667in" height="1.3182436570428697in"}

### 文本文件

打开文件

语法：open(file\[,mode=type,encoding=编码\])，打开指定文件，返回一个文件对象

file，表示待操作文件，相对路径、绝对路径都行（不能是目录）

mode，表示打开文件的方式，如果省略则表示只读模式

r，只读，如果指定的文件不存在系统报错

w，覆盖写入，如果指定的文件不存在，系统会自动创建该文件，然后执行写入操作

a，追加写入，如果指定的文件不存在，系统会自动创建该文件，然后执行写入操作

b，表示二进制，一般用于对图片类的文件操作

encoding，指定编码，（如果打开文件提示编码错误，再加上encoding参数即可）

例1

> ![](media/3rd4tldjgo82ujfkghgv7.png){width="4.166666666666667in" height="2.39501312335958in"}

常用方法

closed，检查文件是否为关闭状态，如果是返回True，否则返回False

close()，关闭文件

encoding，返回打开文件的编码

注意：文件打开后需要关闭

例2

> ![](media/9i6t29d9kwgydcs6s7gr3.png){width="4.166666666666667in" height="2.6608070866141733in"}

读文件

read（），将文件的所有内容读处理，保存在字符串中

readline()，读取文件中的一行，保存在字符串中

readlines（），将文件中所有内容读取出来，保存在列表中，文件中的每一行为列表中的一个元素

> ![](media/ap505yfl3jl3qdvynsj04f.png){width="4.166666666666667in" height="2.424317585301837in"}

写文件

write(s)，将一个字符串写入文件

writelines(iter)，将一个可迭代对象的所有元素写入文件

> ![](media/7zfbmh9vffe7y8k80uob1a.png){width="4.166666666666667in" height="1.8027963692038496in"}

例：

有一个文件保存学生的成绩信息，计算出每个学生的总成绩

> ![](media/qt40vp3iihknd2t7uz51l.png){width="4.166666666666667in" height="1.3387489063867017in"}
>
> ![](media/2xtwjfor0u52tkssk36l28.png){width="4.166666666666667in" height="2.4358431758530186in"}
>
> ![](media/ggv6wgrq7wcn85z00vn39.png){width="4.166666666666667in" height="0.8931813210848644in"}

### with语句

管理上下文，可以实现打开文件后自动关闭

语法:with open(file) as f:

> ![](media/mm9sqdy27xqwm5q2tdgd3.png){width="4.166666666666667in" height="1.6508759842519685in"}

练习

例1：一个目录users，users中使用文件保存用户信息（每个用户一个文件，文件名为账号），文件中包含三行内容，分别是密码、姓名、账号余额，格式如下：

> ![](media/2sp89hinsei9ptbgzpd0rl.png){width="3.0208333333333335in" height="1.0520833333333333in"}

例2：实现系统的登录、注册功能

## 异常

语法：

> ![](media/ju19wbefzbila12egl1cdp.png){width="3.0625in" height="4.163225065616798in"}

try

将有可能引发异常的语句放在try中

except

捕获异常，并且针对该异常进行相应的处理，可以同时存在多个except语句

except 异常，捕获1个指定异常

> ![](media/p7xpadfadf4e90kcuxfc5.png){width="4.166666666666667in" height="2.7285181539807524in"}

except (异常1，异常2，\.....)，捕获元组中的异常

> ![](media/r5lxon2olboa605wzt4sih.png){width="4.166666666666667in" height="2.828021653543307in"}

except Exception，捕获所有的异常

> ![](media/6sllhe7jr4szblmfqpaltm.png){width="4.166666666666667in" height="2.953678915135608in"}

else

如果try中的语句没有引发异常，则执行else后的代码

> ![](media/xbh8xywwlrhs3gzm49rq6.png){width="4.166666666666667in" height="2.764896106736658in"}

finally

无论是否引发异常，finally的代码段都会执行

> ![](media/looywvlb5ba5od0vpmdl6n.png){width="4.166666666666667in" height="2.8982360017497815in"}

raise

主动抛出异常

> ![](media/ggh1shgq1giohhn37gdg9n.png){width="4.166666666666667in" height="3.451123140857393in"}
>
> ![](media/cdvgg5lc0onoysrutrk2jo.png){width="4.166666666666667in" height="2.27in"}

## 数据库操作（重要）

模块：pymysql

pip install pymysql

使用步骤

1、导入pymysql模块

2、调用connect方法连接数据库，返回一个数据库对象

con = pymysql.connect(user=None,password=None,host=None,db=None,port=None,charset=None)

user,数据库用户名

password，数据库用户密码

host，数据库服务器地址

db，要连接的database

port，端口号

charset，字符集

常用方法

cursor()，创建游标

commit()，提交事务

rollback()，回滚事务

close()，关闭数据库连接

3、创建游标

cur = con.cursor(),通过数据库连接对象调用cursor（）方法创建游标，用于执行SQL语句

4、操作数据库

通过游标调用相应的方法执行SQL语句

execute（sql）,执行sql语句，返回该sql语句影响的行数

fetchone()，从select语句的查询结果中返回一行记录

fetchall()，从select语句的查询结果中返回所有记录

close()，关闭游标

5、关闭游标，关闭数据库连接

cur.close()

con.close()

> ![](media/xks94clzj20cgzi48o7az7.png){width="4.166666666666667in" height="1.537671697287839in"}
>
> ![](media/jwm1d9cmfzqfk3ehcswhxn.png){width="4.166666666666667in" height="2.944983595800525in"}

