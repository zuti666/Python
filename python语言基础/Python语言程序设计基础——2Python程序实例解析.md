# Python语言程序设计基础

# 第二章 Python程序示例解析

> 部分截图来自 北京理工大学  嵩天 的python基础设计课程的ppt，仅做个人笔记使用，特此声明。

------

[TOC]

------

# 编程解决问题的步骤

1. 分析问题：分析问题的计算部分，想清楚
2. 划分边界：划分问题的功能边界，规划IPO
3. 设计算法：设计问题的求解算法，关注算法
4. 编写程序：编写问题的计算程序，编程序
5. 调试测试：调试程序使正确运行，运行调试
6. 升级维护：适应问题的升级维护，更新完善



# 代码示例1——温度转换

### 温度转换

> **需求**
>
> 两种温度体系的转换
>
> - 摄氏度转为华氏度
>
> - 华氏度转为摄氏度
>
> 问题分析
>
> 1. 划分边界
>
>    - 输入：带华氏或摄氏标志的温度值
>    - 输出：根据温度标志选择适当的温度转换算法
>
> 2. 输入输出格式设置
>
>    标识放在温度后面，F标识华氏度，C表示摄氏度
>
> 3. 设计算法
>
>    $C=(F-32)/1.8$
>
>    $F=C*1.8+32$
>
> 代码
>
> ```python
> #实例代码1.1 温度转换
> TempStr = input("请输入带有符号的温度值")
> if TempStr[-1] in ['F','f']:
>     C=(eval(TempStr[0:-1])-32)/1.8
>     print("转换后的温度是{:.2f}C".format(C))
> elif TempStr[-1] in ['C','c']:
>     F = 1.8*eval(TempStr[0:-1])+32
>     print("转换后的温度是{:.2f}F".format(F))
> ```
>
> 举一反三
>
> 1. 温度数值与温度标识之间关系的设计可以改变
>
>    标识放在温度数值之前
>
>    ```python
>    TempStr = input("请输入带有符号的温度值")
>    if TempStr[0] in ['F','f']:
>        C=(eval(TempStr[1:])-32)/1.8
>        print("转换后的温度是{:.2f}C".format(C))
>    elif TempStr[0] in ['C','c']:
>        F = 1.8*eval(TempStr[1:])+32
>        print("转换后的温度是{:.2f}F".format(F))
>    ```
>
> 2. 货币转换、长度转换、重量转换、面积转换......
>
>    

## 强缩进

python 与C++,java在代码块的划分是不一样的，C++，java使用{}来区分代码块。而python使用缩进来区分代码块，增强了代码的可读性

## 注释

- 单行注释：单行注释以#开头
- 多行注释：多行注释以‘’’（3个单引号）开头和结尾

## 命名与保留字

变量命名：

- python语言允许采用大写字母，小写字母、数字、下划线_ 和汉字等字符及其组合对变量进行命名。
- 但名字的首字母不能是数字，中间不能出现空格。
- 标识符对大小写敏感
- 变量名不能与python的保留字相同

保留字

| def    | import | from     | as       |
| ------ | ------ | -------- | -------- |
| False  | True   | None     |          |
| if     | elif   | else     | async    |
| for    | while  | break    | continue |
| try    | except | finally  | return   |
| and    | not    | or       | is       |
| assert | with   | raise    | in       |
| del    | global | nonlocal | yiled    |
| pass   | class  | lambda   | await    |

## 字符串

- 创建，python中使用引号‘’创建字符串，不支持单字符类型，单字符在python中也是作为一个字符串来使用

- 访问字符，python使用方括号[]来访问字符串

  - 正向递增序号，最左侧字符为0，向右递增，最右侧字符序号为L-1
  - 反向递减序号，最右侧字符序号为-1，想做依次递减，最左侧字符序号为-L

- 区间访问(切片)，采用[N:M]格式，表示字符串从N到M（不包含M）的子字符串，其中，N和M为字符串的索引序号，可以混合使用正序和逆序序号。如果表示中M或N索引缺失，则表示字符串把开始或结束索引值设置为默认值

- 字符串连接  +

- 判断字符串是否包含给定字符   in   not in 

- 格式化输出 类似于C语言中的sprintf函数  %f 格式化浮点数字，可指定小数后的精度

  

## 列表 [ ]

列表是最常用的Python数据类型，它可以作为一个方括号内的逗号分隔值出现。列表的数据项不需要具有相同的类型。创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。



##  分支

- 使用保留字  if  elif   else 
- 每个保留字所在行最后存在一个冒号(:)，语法的一部分。冒号及后续缩进用来表示后续语句与条件的所属关系



## 输入输出 input print

- input():从控制台获得用户输入的函数

- print():以字符形式向控制台输出结果的函数

  ![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201106095938.png)



## eval()

eval(<字符串>) 能够以Python表达式的方式解析并执行字符串，并将结果输出。eval()函数将去掉字符串的两个引号，将其解释为一个变量。

作用：

1. 处理数字

   单引号、双引号，eval()函数都能将其解释为int类型；三引号解析为str类型。

2. 处理字符串类型的字符串

   对于eval()括号中的字符串（非数字），如果字符串带的是双引号或单引号都会引起NameError，这是因为eval()函数在处理字符串时会去掉两个引号。正确应该使用一个单引号包含一个双引号组成的三引号来包含字符串。

## input 和 eval 结合使用

1. 获得用户输入的数字

   ```python
   value = eval ( input ( "请输入数字：") )
   ```

   

2. 获得用户输入的字符串

   ```python
   Str = eval ( ' input ("请输入字符串") ')
   ```

   



# 思考与练习

2.6 回声程序

> 问题描述：
>
> 请用一行代码·编写一个回声程序，将用户输入的内容直接打印出来
>
> 问题分析：
>
> 获取用户输入：input函数；输出：print函数
>
> 代码：
>
> ```python
> print(input())
> ```

2.7 试想一下，为什么Python的命名不能以数字开头

> 这是为了区分变量和常量。在变量命名可以以数字开头的情况下，无法区分以下内容是定义的变量还是常量：01，2E10。这会在编译的时候造成二义性。所以规定在命名变量的时候不能以数字开头。
>
> 其实，编译器或者解释器都会有一个词法分析器。词法分析器在判断一个单词是否以数字开头，如果是以数字开头则把他当作数字常量处理，否则当作普通单词处理。这样子可以提高词法分析器的效率



# 代码示例2——Python蟒蛇绘制

```python
#示例代码2.1 
import turtle
turtle.setup(650,350,200,200)
turtle.penup()     #笔抬起
turtle.fd(-250)
turtle.pendown()   #笔落下
turtle.pensize(25) #笔的宽度
turtle.pencolor("purple") #笔的颜色
turtle.seth(-40)     #前进方向
for i in range(4):
    turtle.circle(40,80)
    turtle.circle(-40,80)
turtle.circle(40,80/2)
turtle.fd(40)
turtle.circle(16,180)
turtle.fd(40*2/3)
```

## import

import引用函数库

1.  import < 库名 > 

    此时，程序可以调用库名中的所有函数，使用库中函数的格式如下：

    <库名>.<函数名>(<函数参数>)

2. from <库名> import <函数名，函数名，...,函数名>

   from <库名> import *         *是通配符，表示所有函数

   此时，调用该库的函数时不再需要使用库名，直接使用如下格式：

   <函数名>(<函数参数>)

## 循环

- while

  ```python
  while 判断条件:
  	执行语句
  ```

  

- for

  ```python
  for iterating_var in sequence:
  	statements
  ```

  

## range()函数

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109104632.png)



# turtle库

## 1.绘图坐标体系

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201107115019.png)

turtle库绘制图形有一个基本框架：一个小海龟在坐标系中爬行，其爬行轨迹形成了绘制图形。

- turtle.setup(width,height,startx,starty) ： 设置主窗体的大小和位置

  width:窗口的宽度，如果值是整数，表示像素值；如果值是小数，表示窗口宽度与屏幕比例

  height:窗口的高度，如果值是整数，表示像素值；如果值是小数，表示窗口宽度与屏幕比例

  startx:窗口左侧与屏幕左侧的像素距离，如果值是None,窗口位于屏幕水平中央

  starty:窗口顶部与屏幕顶部的像素距离，如果值是None,窗口位于屏幕中央

### turtle绝对坐标系



![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109093408.png)

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109095306.png)

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109095317.png)

### turtle空间坐标系



![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109094924.png)

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109094931.png)

### turtle 角度坐标系

**绝对角度**



![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109095613.png)

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109095710.png)

**海龟角度**

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109095903.png)



## 2.画笔控制函数

- turtle.penup() 别名 turtle.up() ：抬起画笔，之后移动画笔不绘制形状

- turtle.pendown() 别名 turtle.down(): 落下画笔，之后移动画笔将绘制形状

- turtle.pensize(width)  别名 turtle.width()： 设置画笔宽度 ，当无参数时返回当前画笔宽度 

- turtle.pencolor(colorstring)  或turtle.pencolor(r,g,b) : 设置画笔颜色， 当无参数时返回当前画笔颜色

  参数 colorstring ：表示颜色的字符串； （r,g,b）：颜色对应的RGB颜色



## 3.形状绘制函数

- turtle.fd(distance)  别名 turtle.forward(distance) ：向海龟当前行进distance距离

- turtle.seth(to_angle)  别名 turtle.setheading(to_angle)  :设置小海龟当前方向为to_angle，该角度是绝对方向角度值

- turtle.circle(radius,extern=None)  ： 根据半径radius绘制extent角度的弧形  

  参数 ，radius : 弧形半径，值为正数，半径在小海龟左侧；当值为负数时，半径在小海龟右侧。

  ​			extern: 绘制弧形的角度，当不设置参数或参数设置为None,绘制整个圆形

  ![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201109100321.png)

# 函数的封装

通过保留字def定义的函数是自定义函数。

# 思考与练习

2.8 请修改示例代码2.1中第8行，将“purple”变为”violet” ,观察程序运行结果的变化。

> 蟒蛇的颜色发生变化，但是我搜了一下，发现purple和violet在知乎上有着一个很好的回答
>
> https://www.zhihu.com/question/21888107
>
> 代码：
>
> ```python
> # 练习2.8  蟒蛇绘制 改变颜色
> import turtle
> turtle.setup(650,350,200,200)
> turtle.penup()     #笔抬起
> turtle.fd(-250)
> turtle.pendown()   #笔落下
> turtle.pensize(25) #笔的宽度
> turtle.pencolor("violet") #笔的颜色
> turtle.seth(-40)     #前进方向
> for i in range(4):
>     turtle.circle(40,80)
>     turtle.circle(-40,80)
> turtle.circle(40,80/2)
> turtle.fd(40)
> turtle.circle(16,180)
> turtle.fd(40*2/3)
> ```
>
> 

2.9 请修改示例代码2.1中第10行代码，将range(4)变为range(5)，观察程序运行结果的变化。

> 发现蟒蛇的身体相比原来长了一节
>
> 代码：
>
> ```python
> # 练习2.9 蟒蛇绘制 改变蟒蛇长度
> import turtle
> turtle.setup(650,350,200,200)
> turtle.penup()     #笔抬起
> turtle.fd(-250)
> turtle.pendown()   #笔落下
> turtle.pensize(25) #笔的宽度
> turtle.pencolor("purple") #笔的颜色
> turtle.seth(-40)     #前进方向
> for i in range(5):
>     turtle.circle(40,80)
>     turtle.circle(-40,80)
> turtle.circle(40,80/2)
> turtle.fd(40)
> turtle.circle(16,180)
> turtle.fd(40*2/3)
> ```
>
> 

2.10 请球盖示例代码2.1中的第4行和第6行代码，在两行的最前面增加注释符号，即将这两行变成注释语句，观察程序结果的变化

> 海龟首先从原点绘制一条黑线到指定位置
>
> ```python
> # 练习2.10 蟒蛇绘制 改变海龟起落
> import turtle
> turtle.setup(650,350,200,200)
> #turtle.penup()     #笔抬起
> turtle.fd(-250)
> #turtle.pendown()   #笔落下
> turtle.pensize(25) #笔的宽度
> turtle.pencolor("purple") #笔的颜色
> turtle.seth(-40)     #前进方向
> for i in range(4):
>     turtle.circle(40,80)
>     turtle.circle(-40,80)
> turtle.circle(40,80/2)
> turtle.fd(40)
> turtle.circle(16,180)
> turtle.fd(40*2/3)
> ```

2.11 请使用turtle库中的turtle.fd()函数绘制一条直线

> 代码：
>
> ```python
> # 练习2.11 绘制直线
> import turtle
> turtle.fd(500)
> ```
>
> 



2.12  请使用turtle库中的turtle.circle()函数绘制一个完整的圆

> 问题分析：
>
> turtle.circle(radius)函数绘制圆， radius为圆的半径
>
> 代码：
>
> ```python
> # 2.12 绘制完整的圆 
> import turtle
> turtle.circle(100)
> ```
>
> 

2.13 请使用turtle库函数绘制一个包含9个同心圆的靶盘

> 问题分析：
>
> 同心圆，圆心位置相同，圆的半径不一样，
>
> 代码：
>
> ```python
> # 2.13 绘制同心圆
> import turtle
> radius=10
> turtle.circle(10)
> for i in range(1,10):
>     turtle.penup()
>     turtle.seth(-90)
>     turtle.fd(10)
>     radius+=10
>     turtle.seth(0)
>     turtle.pendown()
>     turtle.circle(radius)
> ```
>
> 

# 程序练习题

2.1 实例1的修改。改造实例代码1.1，采用eval(input(<提示内容>))替换现有的输入部分，并使输出的温度值为整数

> 问题分析：
>
> 输出结果不包含小数
>
> 代码：
>
> ```python
> #练习2.1 示例1温度转换的修改
> TempStr = eval('input("请输入带有符号的温度值")')
> if TempStr[-1] in ['F','f']:
>     C=(eval(TempStr[0:-1])-32)/1.8
>     print("转换后的温度是{:.0f}C".format(C))
> elif TempStr[-1] in ['C','c']:
>     F = 1.8*eval(TempStr[0:-1])+32
>     print("转换后的温度是{:.0f}F".format(F))
> ```
>
> 

2.2 汇率兑换程序。按着温度转换程序的设计思路，编写一个美元和人民币的双向兑换程序。

> 需求：
>
> 货币转换，人民币与美元之间的转换
>
> - 人民币转为美元
> - 美元转为人民币
>
> 问题分析
>
> 1. 划分边界
>
>    - 输入：带美元符号或人民币符号的数字
>    - 输出：根据货币标志选择适当的转换算法
>
> 2. 输入输出格式
>
>    使用货币的国际标准符号CNY ，USD
>
> 3. 算法设计
>
>    1美元=6.6116人民币
>
>    1人民币=0.1512美元
>
> 4. 代码
>
>    ```python
>    #练习2.2 汇率兑换程序
>    MoneyStr = input("请输入带有符号的钱数:")
>    #print(MoneyStr[-3:])
>    #print(MoneyStr[0:-3])
>    if MoneyStr[-3:] =='USD':
>        C=eval(MoneyStr[0:-3])*6.6116
>        print("兑换{:.2f}人民币CNY".format(C))
>    elif MoneyStr[-3:] =='CNY':
>        U = eval(MoneyStr[0:-3])*0.1512
>        print("兑换{:.2f}美元USD".format(U))
>    ```
>
>    



2.3 实例2的修改。改造示例代码2.1，绘制一条彩色蟒蛇，及在绘制Python蟒蛇的每个小段时，画笔的绘制颜色会发生改变。提示：将画笔颜色控制函数放在蟒蛇绘制函数附近。

> 设计：
>
> 把颜色改变的代码放在绘制图形的循环之中
>
> 颜色可以使用（r,g,b），改变r,g,b的数值就可以改变颜色。颜色可以根据循环变量i改变，也可以通过随机数来改变。
>
> 也可以设置一个列表存放不同的color单词，根据i从列表中选择
>
> 代码：
>
> ```python
> #练习2.3 示例2蟒蛇绘制 的修改 
> import turtle
> turtle.setup(650,350,200,200)
> turtle.penup()     #笔抬起
> turtle.fd(-250)
> turtle.pendown()   #笔落下
> turtle.pensize(25) #笔的宽度
> turtle.seth(-40)     #前进方向
> for i in range(4):
>  turtle.pencolor((255-i*40),(32+i*10),(100+i*24)) #笔的颜色
>  turtle.circle(40,80)
>  turtle.circle(-40,80)
> turtle.circle(40,80/2)
> turtle.fd(40)
> turtle.circle(16,180)
> turtle.fd(40*2/3)
> ```
>
> 



2.4 等边三角形的绘制。使用turlte库中的turtle.fd()函数和turtle.seth()函数绘制一个等边三角形。

> 分析：等边三角形的角度为60度，设置turtle相应的前进方向
>
> 代码：
>
> ```python
> #练习2.4 绘制等边三角形
> import turtle
> 
> turtle.fd(100)
> turtle.seth(120)
> turtle.fd(100)
> turtle.seth(240)
> turtle.fd(100)
> ```
>
> 反思：
>
> turtle设置方向可以根据绝对坐标也可以根据相对坐标
>
> ```
> import turtle
> 
> for i in range(3):
>     turtle.fd(100)
>     turtle.left(120)
> ```
>
> 



2.5 叠加三角形的绘制。使用turtle库中的turtle.fd()函数和tuetle.seth()函数绘制一个叠加等边三角形。

> 分析：叠加三角形相当于三个三角形的叠加，可以将绘制一个正三角形的操作封装在函数中
>
> 代码;
>
> ```python
> #练习2.5 绘制叠加三角形
> import turtle
> def Tri():
>  turtle.seth(0)
>  turtle.fd(100)
>  turtle.seth(120)
>  turtle.fd(100)
>  turtle.seth(-120)
>  turtle.fd(100)
>  
> Tri()
> turtle.fd(100)
> Tri()
> turtle.seth(0)
> turtle.fd(100)
> Tri()
> ```
>
> 反思：
>
> 可以设置相对坐标
>
> 叠加三角形还可以看做是大三角形中嵌套小三角形
>
> ```python
> #练习2.5 绘制叠加三角形
> import turtle
> #先绘制大三角形
> turtle.seth(0)
> for i in range(3):
>     turtle.fd(200)
>     turtle.left(120)
> 
> turtle.left(60)
> turtle.fd(100)
> #再绘制小三角形
> turtle.seth(0)
> for i in range(3):
>     turtle.fd(100)
>     turtle.right(120)
> ```
>
> 

2.6 无角正方形的绘制。利用turle库函数绘制一个没有角的正方形。

> 分析：没有角的效果可以通过控制海龟升起和降落来实现
>
> 代码：
>
> ```python
> #练习2.6 绘制没有角的正方形
> import  turtle
> 
> def Line():
>     turtle.penup()
>     turtle.fd(20)
>     turtle.pendown()
>     turtle.fd(60)
>     turtle.penup()
>     turtle.fd(20)
> 
> for i in range(4):
>     turtle.seth(90*i)
>     Line()
> 
> ```
>
> 

2.7六芒星的绘制。利用turle库函数绘制一个六芒星。

> 分析：六边形可以看做是两个大正三角形叠加的结果，而且两个大三角形仅在初始角度相差60度；
>
> 代码：
>
> ```python
> #练习2.7 绘制六边形
> import  turtle
> 
> def Tri(i):
>  turtle.seth(0+i)
>  turtle.fd(300)
>  turtle.seth(120+i)
>  turtle.fd(300)
>  turtle.seth(240+i)
>  turtle.fd(300)
> 
> Tri(30)
> turtle.seth(30)
> turtle.fd(200)
> turtle.seth(270)
> turtle.fd(100)
> Tri(90)
> ```
>
> 反思：可以采用相对角度来绘制三角形
>
> ```
> #练习2.7 绘制六边形
> import  turtle
> 
> def Tri():
>  turtle.fd(300)
>  turtle.left(120)
>  turtle.fd(300)
>  turtle.left(120)
>  turtle.fd(300)
> 
> turtle.left(30) #六芒星摆放的角度
> 
> Tri()
> turtle.left(120)
> turtle.fd(200)
> turtle.right(120)
> turtle.fd(100)
> turtle.left(180)
> Tri()
> ```
>
> 

2.8 正方形螺旋线的绘制。利用turle库函数绘制一个正方形螺旋线。

> 分析：正方形螺旋形是个边长不断变大的正方形，只有两条边是相同长度的
>
> 代码：
>
> ```python
> #练习2.7 绘制正方形螺旋线
> import  turtle
> 
> def Squ(angle,length):
>  turtle.seth(0+angle)
>  turtle.fd(length)
>  turtle.seth(90+angle)
>  turtle.fd(length)
> 
> for i in range(20):
>  if i % 2 == 1 :
>      Squ(90,i*10)
>      turtle.seth(270)
>      Squ(270,(i+1)*10)
> ```
>
> 反思：
>
> 使用相对坐标
>
> ```python
> #练习2.7 绘制正方形螺旋线
> import  turtle
> 
> def Squ(length):
>  turtle.left(90)
>  turtle.fd(length)
>  turtle.left(90)
>  turtle.fd(length)
> 
> for i in range(20):
>     Squ(i*10)
> ```
>
> 

2.9 自定义Python蟒蛇绘制。





# Python123练习

练习程序设计题

## 练习1

1 温度转换

> 问题描述：和课上讲解示例相同
>
> 代码：
>
> ```python
> TempStr = eval('input()')
> if TempStr[-1] in ['F','f']:
>     C=(eval(TempStr[0:-1])-32)/1.8
>     print("{:.2f}C".format(C))
> elif TempStr[-1] in ['C','c']:
>     F = 1.8*eval(TempStr[0:-1])+32
>     print("{:.2f}F".format(F))
> else:
>     print("输入格式错误")
> ```
>
> 



2 Hello World

> 问题描述:输出Hello World
>
> 代码：
>
> ```python
> #输出Hello World
> print("Hello World")
> ```
>
> 

3  数字形式转换 1

> 问题描述：获得用户输入的一个正整数输入，输出该数字对应的中文字符表示。‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 0到9对应的中文字符分别是：零一二三四五六七八九
>
> 问题分析： 读取用户的输入，可以设置一个列表，输入根据列表来一一对应进行转换
>
> 代码：
>
> ```python
> #数字形式转换
> Zhong = ["零","一","二","三","四","五","六","七","八","九"]
> Shu = ["0","1","2","3","4","5","6","7","8","9"]
> Cin = input()
> Cout = ""
> for i in range(  len(Cin) ):
>     if Cin[0] in Zhong:
>         for j in range(10):
>             if Cin[i] == Zhong [j]:
>                 Cout = Cout +   Shu[j]
>     else:
>        for j in range(10):
>             if Cin[i] == Shu [j]:
>                 Cout = Cout +   Zhong[j]
> print(Cout) 
> ```
>
> 反思：
>
> 读题错误，只要求输入正整数来获得中文字符输出
>
> 参考代码：
>
> ```python
> template = "零一二三四五六七八九"
> 
> s = input()
> for c in s:
>     print(template[eval(c)], end="")
> ```
>
> 

4.温度转换二 

> 问题描述：
>
> 要求如下：‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> (1) 输入输出的摄氏度采用大写字母C开头，温度可以是整数或小数，如：C12.34指摄氏度12.34度；‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> (2) 输入输出的华氏度采用大写字母F开头，温度可以是整数或小数，如：F87.65指华氏度87.65度；‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> (3) 不考虑异常输入的问题，输出保留小数点后两位；‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> (4) 使用input()获得测试用例输入时，不要增加提示字符串。
>
> 主要区别是温度表现形式不一样
>
> 代码：
>
> ```python
> #温度转换2 
> TempStr = input()
> if TempStr[0] == 'F':
>     C=(eval(TempStr[1:])-32)/1.8
>     print("C{:.2f}".format(C))
> elif TempStr[0] == 'C':
>     F = 1.8*eval(TempStr[1:])+32
>     print("F{:.2f}".format(F))
> ```
>
> 参考代码：
>
> ```python
> #TempConvert.py
> TempStr = input()
> if TempStr[0] in ['F']:
>     C = (eval(TempStr[1:]) - 32)/1.8
>     print("C{:.2f}".format(C))
> elif TempStr[0] in ['C']:
>     F = 1.8*eval(TempStr[1:]) + 32
>     print("F{:.2f}".format(F))
> else:
>     print() #不输入任何错误提示
> ```
>
> 

## 练习2 

1 蟒蛇绘制

> 问题描述：
>
> 与课上讲解实例相同
>
> 代码：
>
> ```python
> #示例代码2.1 
> import turtle
> turtle.setup(650,350,200,200)
> turtle.penup()     #笔抬起
> turtle.fd(-250)
> turtle.pendown()   #笔落下
> turtle.pensize(25) #笔的宽度
> turtle.pencolor("purple") #笔的颜色
> turtle.seth(-40)     #前进方向
> for i in range(4):
>     turtle.circle(40,80)
>     turtle.circle(-40,80)
> turtle.circle(40,80/2)
> turtle.fd(40)
> turtle.circle(16,180)
> turtle.fd(40*2/3)py
> ```
>
> 

2.绘制正方形

> 问题描述：
>
> 绘制正方形
>
> 代码：
>
> ```python
> import turtle
> 
> for i in range(4):
>     turtle.fd(100)
>     turtle.left(90)
> ```
>
> 

3 绘制正六边形

> 问题描述：绘制正六边形
>
> 代码：
>
> ```python
> #练习2.7 绘制正六边形
> import  turtle
> 
> for i in range(6):
>   turtle.fd(100)
>   turtle.left(60)
> ```
>
> 

4 绘制叠加形状

> 问题描述：
>
> 代码：
>
> ```python
> #TwoRoundDraw.py
> import turtle as t
> Color = ["black","red","green","orange","blue","violet","yellow","gold","grey"]
> t.pensize(2)
> for i in range(9):
>     t.pencolor(Color[i])
>     t.fd(150)
>     t.left(80)  #720/9
> ```
>
> 

## 测试1

1  Hello World的条件输出

> 问题描述：
>
> 获得用户输入的一个整数，参考该整数值，打印输出"Hello World"，要求：‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 如果输入值是0，直接输出"Hello World"‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 如果输入值大于0，以两个字符一行方式输出"Hello World"（空格也是字符）‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 如果输入值小于0，以垂直方式输出"Hello World"
>
> 我的解答：
>
> ```python
> Cin = eval(input())
> H = "Hello World"
> Length = len( H )
> if Cin == 0 :
>     print("Hello World")
> elif Cin > 0 :
>     for i in range(Length+1):
>          if ( i % 2 ) == 1: 
>              print ( H[i-1:i+1])
>         
> else:
>     for j in range(Length):
>         print ( H[j] )
> ```
>
> 参考答案：
>
> ```python
> n = eval(input())
> if n == 0:
>     print("Hello World")
> elif n > 0:
>     print("He\nll\no \nWo\nrl\nd")
> else:
>     for c in "Hello World":
>         print(c)
> ```
>
> 反思：
>
> python 的for 循环是有着 类似java的迭代器的功能
>
> \n表示换行

2  数值运算

> 问题描述：
>
> 获得用户输入的一个字符串，格式如下：‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> M OP N‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 其中，M和N是任何数字，OP代表一种操作，表示为如下四种：+, -, *, /（加减乘除）‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 根据OP，输出M OP N的运算结果，统一保存小数点后2位。‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬
>
> 注意：M和OP、OP和N之间可以存在多个空格，不考虑输入错误情况。
>
> 我的解答：
>
> ```python
> cin = input()
> length =  len(cin)
> index=0
> for i in range(length):
>     if cin[i] != " " and (not cin [i].isnumeric() and cin[i] != "-" and cin[i] != "." and cin[i] !="x"):
>         index = index+i
> M = eval(cin[0:index])
> OP = cin[index]
> N = eval(cin[index+1:length+1])
> if OP == "+":
>     print('%.2f'%(M+N))
> elif OP == "-":
>     print('%.2f'%(M - N))
> elif OP == "*":
>     print('%.2f'%(M * N))
> elif OP == "/":
>     print('%.2f'%(M / N))
> ```
>
> 参考答案：
>
> ```python
> s = input()
> print("{:.2f}".format(eval(s)))
> ```
>
> 反思：
>
> 可能是受之前的编程思想限制了，感觉自己就像是个白痴

## 测试2

1 绘制八边形

> 问题描述：
>
> 使用turtle库，绘制一个八边形
>
> 参考代码：
>
> ```python
> import turtle as t
> t.pensize(2)
> for i in range(8):
>     t.fd(100)
>     t.left(45)
> ```
>
> 

2  绘制八角星

> 问题描述：
>
> 使用turtle库，绘制一个八角图形。
>
> 代码参考：
>
> ```python
> import turtle as t
> t.pensize(2)
> for i in range(8):
>     t.fd(150)
>     t.left(135)
> ```
>
> 





