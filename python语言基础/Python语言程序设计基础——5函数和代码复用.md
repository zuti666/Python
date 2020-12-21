# Python语言程序设计基础

# 第5章 函数和代码复用

------

[TOC]

------

## 函数的基本使用

### **函数的定义**

函数是一段具有特定功能的、可重用的语句组，用函数名表示并通过函数名进行功能调用。

使用函数主要有两个目的：降低编程难度和代码重用。

Python使用def定义一个函数，语法形式：

```python
def <函数名> (<参数列表>):
	<函数体>
	return <返回值列表>
```

函数调用和执行的一般形式

```python
<函数名>(<参数列表>)
```

### lambda函数

lambda用于定义一种特殊的函数——匿名函数，又称为lambda函数。匿名函数并非没有名字，而是将函数名作为函数结果返回，语法格式如下

```python
<函数名> = lambda <参数列表> : <表达式>
lambda 函数与正常函数一样，等价于如下形式：
def <函数名> (<参数列表>):
    return <表达式>
```

```python
f =  lambda x,y : x+y 
print(type(f))
print(f(10,20))
```



## 函数的参数传递

### **可选参数与可变数量参数**

可以定义函数时直接为这些参数指定默认值，当函数被调用时，如果没有传入对应的参数值，则使用函数定义时的默认值代替。由于函数调用时需要按顺序输入参数，可选参数必须定义在非可选参数的后面。

```python
def dup (str , times = 2):
    print(str * times)
dup("konck~")
```

在函数定义时，也可以设计可变数量参数，通过在参数前增加星号(*)实现。带有星号的可变参数只能出现在参数列表的后面。调用时，这些参数被当做元组类型传递到参数中，实例如下：

```python
def vfunc(a, *b ):
    print(type(b))
    for n in b:
         print(n,end='')
        a += n
    return a
vfunc(1,2,3,4,5,6)
```



### 参数的位置和名称传递

函数调用时，实参默认采用按着位置的顺序的方式传递给函数

Python还提供了按着形参名称传入实参的方式，由于调用函数时指定了参数名称，所以参数之间的顺序可以任意调整。



### 函数的返回值

return语句用来退出函数并将函数返回到函数被调用的位置继续执行。函数可以没有return，此时函数不返回值。函数也可以用return返回多个值，多个值以元组类型保存。

```python
def func(a,b):
    return b,a
a = func("knock~",2)
print(a,type(a))
```



### 函数对变量的改变

全局变量是指在函数之外定义的变量，一般没有缩进，在程序执行全过程有效。

局部变量是指在函数内部使用的变量，仅在函数内部使用变量，仅在函数内部有效，当函数退出时变量将不存在。

1. 简单数据类型变量无论是否与全局变量重名，仅在函数内部创建和使用，函数退出后变量被释放，如有全局变量，其值不变。

2. 简单数据类型变量在用global保留字声明后，作为全局变量使用，函数退出后该变量保留且值被函数改变。

3. 对于组合数据类型的全局变量，如果在函数内部没有被真实创建的同名变量，则函数内部可以直接使用并修改全局变量的值。

4. 如果函数内部真实创建了组合数据类型变量，无论是否有同名全局变量，函数仅对局部变量进行操作，函数退出后局部变量被释放，全局变量值不变。

   



## 模块3 ：datetime库的使用

**datetime库概述**

datetime库可以从系统中获得时间，并以用户选择的格式输出。

datetime库以格林威治时间为基，每天由3600*24秒精确定义。该库包括两个常量：datetime.MINYEAR和datetime.MXYEAR，分别表示datetime所能代表的最小，最大年份，值分别为1与9999。

datetime.datetime类表达形式最为丰富。引入datetime类的方式如下:

```python
from datetime import datetime
```

**datetime类的使用**

datetime类的使用是首先创建一个datetime对象，然后通过对象的方法和属性显示时间。

创建datetime对象有三种方法：datetime.now(),dtetime.utcnow(),datetime.datetime()

1. datetime.now() ,返回一个datetime类型，表示当前日期和时间，精确到微秒

   ```python
   from datetime import datetime
   today = datetime.now()
   today
   ```

   

2. datetime.utcnow()，返回一个datetime类型，表示当前日期和时间的UTC表示，精确到微秒

   ```python
   today = datetime.utcnow()
   today
   ```

   

3. datetime(year,month,day,hour=0,minute=0,second=0,microsecond=0)构造一个日期和时间对象

   ```python
   someday = datetime(2017,9,1,10,30,34,2)
   someday
   ```

**datetime类对象的常见属性 9个**

| 属性                 | 描述 |
| -------------------- | ---- |
| datetime.min         |      |
| datetime.max         |      |
| datetime.year        |      |
| datetime.month       |      |
| datetime.day         |      |
| datetime.hour        |      |
| datetime.minute      |      |
| datetime.second      |      |
| datetime.microsecond |      |

**date类常用的时间格式化方法 3 个**

| 属性                  | 描述                                        |
| --------------------- | ------------------------------------------- |
| datetime.isoformat()  | ISO 8601 标准显示时间                       |
| datetime.isoweekday() | 根据日期计算星期后返回1~7对应星期一到星期日 |
| datetime.strftime()   | 根据格式化字符串format进行格式显示的方法    |

strtime()方法是时间格式化最有效的方法，几乎可以以任何通用格式输出时间

**strftime()方法的格式控制符**

| 格式化字符串 | 日期/时间  | 值范围和实例 |
| ------------ | ---------- | ------------ |
| %Y           | 年份       |              |
| %m           | 月份       |              |
| %B           | 月名       |              |
| %b           | 月名缩写   |              |
| %d           | 日期       |              |
| %A           | 星期       |              |
| %a           | 星期缩写   |              |
| %H           | 小时（12） |              |
| %I           | 小时（24） |              |
| %p           | 上/下午    |              |
| %M           | 分钟       |              |
| %S           | 秒         |              |

### 思考与练习

请利用datetime库将当前系统时间转换为字符串

```python
from datetime import datetime
today = datetime.utcnow()
str=today.strftime("%Y-%m-%d  %H:%M:%S")
print(str)
```

请利用datetime库输出5种不同的日期格式

```

```

思考如何利用datatime库对一个程序的运行计时。





## 实例7： 七段数码管绘制

IPO描述

> 输入：当前日期的数字形式
>
> 处理：根据每个数字绘制七段数码管表示
>
> 输出：绘制当前日期的七段数码管表示

代码：

```python
#七段数码管绘制
import turtle, datetime
#绘制数码管间隔
def drawGap():
    turtle.penup()
    turtle.fd(5)
#绘制单段数码管
def drawLine(draw):
    drawGap()
    turtle.pendown() if draw else turtle.penup()
    turtle.fd(40)
    drawGap()
    turtle.right(90)
#根据数字绘制七段数码管
def drawDigit(d):
    drawLine(True) if d in [2,3,4,5,6,8,9] else drawLine(False)
    drawLine(True) if d in [0,1,3,4,5,6,7,8,9] else drawLine(False)
    drawLine(True) if d in [0,2,3,5,6,8,9] else drawLine(False)
    drawLine(True) if d in [0,2,6,8] else drawLine(False)
    turtle.left(90)
    drawLine(True) if d in [0,4,5,6,8,9] else drawLine(False)
    drawLine(True) if d in [0,2,3,5,6,7,8,9] else drawLine(False)
    drawLine(True) if d in [0,1,2,3,4,7,8,9] else drawLine(False)
    turtle.left(180)
    turtle.penup()
    turtle.fd(20)
def drawDate(date):
    turtle.pencolor("red")
    for i in date:
        if i == '-':
            turtle.write('年',font=("Arial",18,"normal"))
            turtle.pencolor("green")
            turtle.fd(40)
        elif i == '=':
            turtle.write('月',font=("Arial",18,"normal"))
            turtle.pencolor("blue")
            turtle.fd(40)
        elif i == '+':
            turtle.write('日',font=("Arial",18,"normal"))
        else:
            drawDigit(eval(i))
def main():
    turtle.setup(800,350,200,200)
    turtle.penup()
    turtle.fd(-350)
    turtle.pensize(5)
    drawDate(datetime.datetime.now().strftime('%Y-%m=%d+'))
    turtle.hideturtle()

main()

```



##  代码复用和模块化设计

当代编程语言从代码层面采用函数和对象两种抽象方式，分别对应面向过程和面向对象编程思想

函数是程序的一种基本抽象方式。函数封装的直接好处是代码复用，当更新函数功能时，所有被调用的功能都被更新。

对象是程序的一种高级抽象方式，他将程序代码组织为更高的类。对象它包含表征对象特征的·属性和代表对象操作的方法。



模块化设计 是使用函数和对象设计程序的思考方法，以功能块为基本单位，一般有两个基本要求。

1. 紧耦合：尽可能合理划分功能块，功能块内部耦合紧密
2. 松耦合：模块间关系尽可能简单，功能块之间耦合度低

耦合是指程序结构中各模块之间相互关联的程度。



## 函数的递归

函数中定义调用的函数自身的方式称为递归。

**经典递归例子——阶乘**
$$
 n! = 
\begin{cases}
 1          &n=0             \\
 n(n-1)!    &otherwise \\
\end{cases}
$$
代码：

```python
def fact(n):
    if n==0 :
        return 1
    else:
        return n * fact(n-1)
num = eval(input("请输入一个整数"))
print(fact(abs(int(num))))
```



**字符串反转**

```python
def reverse(s):
    if s == "":
        return s
    else:
        return reverse(s[1:])+ s[0]
str = input ("请输入一个字符串： ")
print(reverse(str))str = input ("请输入一个字符串： ")
print(str[::-1])
```



```python
str = input ("请输入一个字符串： ")
print(str[::-1])
```



当Python递归调用到1000层，解析器将终止程序。用户可以通过以下代码设定

```python
import sys
sys.setrecursionlimit(2000)
```



## 实例8 科赫曲线绘制



科赫曲线在众多经典数学数学曲线中非常著名，由瑞典数学家科赫于1904年提出，其形状类似于雪花，也被称雪花曲线。

科赫曲线的基本概念和绘制方法如下。

> 正整数n代表科赫曲线的阶数，表示生成科赫曲线过程的操作次数。
>
> 科赫曲线初始化阶数为0，表示一个长度为L的直线。对于直线L，将其等分为3段，中间一段用边长为L/3的等边三角形的两个边代替，得到一阶科赫曲线，它包含4条线段。
>
> 进一步对每条线段重复同样的操作后得到2阶科赫曲线，继续重复同样的操作n次就可以得到n阶科赫曲线。
>
> 

科赫曲线属于分形几何分支，它的绘制过程体现了递归思想，其代码如下：

```python
# 科赫曲线绘制
import turtle
def koch(size,n):
    if n== 0 :
        turtle.fd(size)
    else:
        for angle in [0,60,-120,60]:
            turtle.left(angle)
            koch(size/3,n-1)
def main():
    turtle.setup(800,400)
    turtle.speed(0)  #控制速度
    turtle.penup()
    turtle.goto(-300,-50)
    turtle.pendown()
    turtle.pendown()
    turtle.pensize(2)
    koch(600,3) #0阶科赫曲线长度，阶数
    turtle.hideturtle()
main()
```

图形

```python
#漂亮图形
import turtle
def koch(size,n):
    if n== 0 :
        turtle.fd(size)
    else:
        for angle in [0,60,-120,60]:
            turtle.left(angle)
            koch(size/3,n-1)
def main():
    turtle.setup(600,600)
    turtle.speed(10)
    turtle.penup()
    turtle.goto(-200,100)
    turtle.pendown()
    turtle.pensize(2)
    level=5
    koch(400,level)
    turtle.right(120)
    koch(400,level)
    turtle.right(200)
    koch(400,level)
    turtle.hideturtle()
main()
```





## Python内置函数

|      |      |      |      |      |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |





## 程序练习题







## Python123