# 四 程序的控制结构

------

[TOC]



## 基本结构

### 程序流程图

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201125064448.jpg)

程序描述方式主要有三种，分别是自然语言，流程图，伪代码。

、

## 分支结构

### 单分支 if

 **微实例 4.4  PM2.5空气质量提醒**

> **问题描述**：
>
> 目前空气质量等级以PM2.5数值划分为6级，PM2.5数值在0~35空气质量为优，3 5~75为良， 75~115为轻度污染， 115~150为中度污染， 150~250为重度污染， 250~500为严重污染，。
>
> 一个简化版的空气质量标准采用三级模式：0~35空气质量为优，3 5~75为良， 75以上为污染。
>
> **问题分析**：
>
> IPO描述
>
> 输入：接受外部输入的	PM2.5 值
>
> 处理：
>
> ​		if PM2.5 值  >= 75 ,打印空气污染警告
>
> ​		if 35 <= PM2.5值 <  75 ，打印空气质量良，建议适度户外活动
>
> ​		if PM2.5值 < 35 ，打印空气质量优，建议户外活动
>
> **代码**：
>
> ```python
> #微实例4.4
> PM = eval(input("请输入PM2.5 数值： "))
> if 0 <= PM <= 35:
>     print("空气优异，快去户外运动")
> if 35 <= PM <= 75:
>     print("空气良好，适度户外活动")
> if 75 <= PM:
>     print("空气污染，请小心！")
> ```
>
> 

### 二分支结构： if-else 语句

 **微实例 4.5  PM2.5空气质量提醒（2**）

> 代码：
>
> ```python
> #微实例 4.5
> PM = eval(input("请输入PM2.5数值： "))
> if PM >= 75:
>     print("空气污染，请小心！")
> else:
>     print("空气没有污染，可以展开户外活动")
> ```
>
> 代码：
>
> ```python
> PM = eval(input("请输入PM2.5数值： "))
> print(f'空气{"存在" if PM  >=75 else "没有"} 污染！')
> ```
>
> 



### 多分支结构： if-elif-else 语句

**微实例 4.46 PM2.5空气质量提醒（3）**

------

> 代码:
>
> ```python
> PM = eval(input("请输入PM2.5数值："))
> if 0<= PM <=35:
>     print("空气优异，快去户外活动！")
> elif 35 <= PM <= 75:
>     print("空气良好，适度户外活动！")
> else:
>     print("空气污染，请小心！")
> ```
>
> 
>

## 实例5： 身体质量指数

> 问题描述：
>
> $BMI = 体重(kg) / 身高^{2}(m^2)$
>
> BMI指标分类
>
> | 分类 | 国际BMI值($kg/m^2$) | 国内BMI值($kg/m^2$) |
> | ---- | ------------------- | ------------------- |
> | 偏瘦 | <18.5               | <18.5               |
> | 正常 | 18.5 ~ 25           | 18.5~24             |
> | 偏胖 | 25~ 30              | 24 ~ 28             |
> | 肥胖 | >=30                | > = 28              |
>
> 编写一个根据身高体重计算BMI值的程序，同时输出国际和国内的BMI指标建议值。
>
> 问题分析：
>
> IPO描述
>
> 输入：身高和体重值
>
> 处理：计算BMI值，并根据BMI指标分类找到合适类别
>
> 输出L打印指标分类信息
>
> 代码：
>
> ```python
> #示例代码5.1
> height , weight = eval(input("请输入身高（m)和体重（kg)[逗号隔开]： "))
> bmi = weight / pow(height,2)
> print(f'BMI数值为：{bmi:.2f}')
> who , dom = "", ""
> # WHO标准
> if bmi < 18.5:
>     who = "偏瘦"
> elif bmi < 25:
>     who ="正常"
> elif bmi <30:
>     who = "偏胖"
> else:
>     who = "肥胖"
> 
> #我国卫生部标准
> if bmi < 18.5:
>     dom = "偏瘦"
> elif bmi < 24:
>     dom ="正常"
> elif bmi <28:
>     dom = "偏胖"
> else:
>     dom = "肥胖"
> 
> print(f'BMI指标为： 国际{who}，国内{dom}')
> ```
>
> 

## 循环结构



### 遍历循环 for

`for <循环变量> in <遍历结构> :
	<语句块> `

遍历结构可以是字符串，文件，组合数据类型或range()函数等，常见的使用方式如下：

`循环N次
for i in range(N):
	<语句块>`

`遍历文件fi的每一行
for line in fi:
	<语句块>`

`遍历字符串s
for c in s:
	<语句块>`

`遍历列表ls
for item in ls:
	<语句块>`

循环遍历还有一种扩展模式

```python
for <循环变量> in <遍历结构>:
	<语句块1>
else:
	<语句2>
```

 在这种扩展模式中，当for循环正常执行之后，程序会继续执行else语句中的内容。else语句只在循环征程执行并结束才执行。

```python
for s in "BAT":
    print("循环执行中"+s)
else:
     s ="循环正常结束"
print(s)
```



### 无限循环 while

```python
while <条件> :
	<语句块>
```

扩展方式

```python
while <条件> :
	<语句块1>
else:
	<语句块2>
```

```python
s , idx = "BAT" ,0
while idx < len(s):
    print("循环进行中："+s[idx])
    idx += 1
else:
    s = "循环正常结束"
print(s)
```



### 循环保留字 break 和  continue

break 跳出当前层次循环，结束整个循环过程，不再判断执行循环的条件是否成立。

continue 用来结束当前当次循环，即跳出循环体下面尚未执行的语句，但不跳出当前循环，只结束本次循环，而不终止整个循环的执行。

```python
for s in "PYTHON":
    if s=="T":
        continue
    print(s,end='')
    
for s in "PYTHON":
    if s=="T":
        break
    print(s,end='')
```

 for循环和while循环中都存在一个else扩展用法。else中的语句只在一种条件下执行，即循环正常遍历了所有内容或由于条件不成立二结束循环，没有因为break或return而退出。continue保留字对else没有影响。

```python
for s in "PYTHON":
    if s == "T":
        continue
    print(s,end='')
else:
    print("正常退出")
  
for s in "PYTHON":
    if s == "T":
        break
    print(s,end='')
else:
    print("正常退出")
```









## 模块2：random库的使用

**概述**

 random库次用梅森旋转算法(Mersenne Twister)生成伪随机序列，可用于除随机性要求更高的加解密算法之外的大多数工程应用。

**random 库常用的随机函数** 共9个

| 函数                          | 描述                                             |
| ----------------------------- | ------------------------------------------------ |
| seed(a=None)                  | 初始化随机数种子                                 |
| random(m)                     | 生成一个【0.0,1.0】之间的随机小数                |
| randint(a,b)                  | 生成一个【a,b]之间的整数                         |
| getrandbits(k)                | 生成一个k比特长度的随机整数                      |
| randrange(start,stop,[,step]) | 生成一个【start，stop]之间以step为步数的随机整数 |
| uniform(a,b)                  | 生成一个【a,b]之间的随机小数                     |
| choice(seq)                   | 从序列类型，例如列表中随机返回一个元素           |
| shuffle(seq)                  | 将序列类型中的元素随机排列，返回打乱后的序列     |
| sample(pop,k)                 | 从pop类型中随机选取k个元素，以列表类型返回       |

生成随机数钟子之前可以通过seed()函数指定随机数种子，随机数种子1一般是一个整数，只要种子相同，每次生成的随机数序列也相同。

### 思考与练习

4.18 从randon库中选取相应的函数满足下列条件。

1 随机生成100以内的10个整数

2 随机选取0到100间的奇数

3 从字符串‘abcdefghij’中随机选取4个字符

4 随机选取列表[‘apple’,’pear’,’peach’,’orange’]中的一个字符串

```python
from random import *

print(sample(range(100),10))
while(1):
    a=randint(0,100)
    if a %2 == 1 :
        print(a)
        break
print(sample('abcdefghij',4))
print(choice(['apple','pear','peach','orange']))
```



## 实例6： $\pi$的计算

蒙特卡洛方法，又称随机抽样统计试验方法。当所要求解的问题是某种事件出现的概率，或者是某个随机变量的期望值时，它们可以通过某种‘试验’的方法，得到这种事件发生的频率，或者这个随机变量的平均值，并用它们作为问题的解。这就是蒙特卡罗法的基本思想。

蒙特卡洛求$\pi$的就是随机向单位正方形和圆中泡随机点，计算每个点到圆心的距离从而判断该店在园内或者圆外，用圆内的点数除以总点数就是$\pi$值。随机点数量越大，越充分覆盖整个圆形，计算得到的$\pi$值越精确。这个方法的思想是利用离散点值表示图形的面积，通过面积比例来求解$\pi$值。

> IPO描述：
>
> 输入：抛点数
>
> 处理：计算每个点到圆心的距离，统计在圆心点的数量
>
> 输出：$\pi$值
>
> 代码：
>
> ```python
> # 示例代码 6.1 蒙特卡洛计算pi
> from random import random
> from math import sqrt
> from time import clock
> 
> DARTS =10000
> hits = 0.0
> clock()
> for i in range(1,DARTS+1):
>     x ,y = random() , random()
>     dist = sqrt(x**2 + y**2)
>     if dist <= 1.0:
>         hits = hits + 1
> pi = 4 * (hits / DARTS)
> print(f'Pi值是{pi}')
> print(f'运行时间是：{clock():5.5} s')
> ```
>
> 



## 异常处理

### try-except

```python
num=eval(input("请输入一个整数： "))
print(num)
```

Python异常信息含义说明 

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201127201648.png)

Python 使用· try -except语句实现异常，其基本语法格式如下

```python
try:
	<语句块1>
except <异常类型>:
	<语句块2>
```

代码改进

```python
try:
    num=eval(input("请输入一个整数： "))
    print(num)
except NameError:
    print("输入错误，请输入一个整数")
```



### try  except else finally

try - except 语句支持多个except语句，其语法格式如下

```python
try:
    <语句块1>
except <异常类型1>:
    <语句块2>
    。。。
    
except <异常类型N> :
    <语句块N+1>
except:
    <语句块N+2>
```

其中，第一个到第N个except语句后面都指定了异常类型，说明这些except所包含的语句块只处理这些类型的异常。最后一个except没有指定任何类型，表示它对应的语句块可以处理所有其他异常。

异常语句还可以与else和finally配合使用，语法格式如下

```python
try:
    <语句块1>
except <异常类型1>:
    <语句块2>
else :
    <语句块3>
finally:
    <语句块4>
```

此处的else语句与for循环和while循环中的else一样，当try中的语句块正常执行结束且没有发生异常时,else中的语句块3执行，可以看作是对try语句块正常执行后的一种追加处理。finnally语句块，无论try语句块1是否发生异常都会执行，可以将程序执行语句块1的一些收尾工作放在这里，例如，关闭文件等。





## 程序练习题

4.1 猜数游戏 。从程序中预设一个0~9之间的整数，让用户输入所猜的数字，如果大于预设的数字，显示“遗憾，太大了”；小于预设的数，显示”遗憾，太小了“,如此循环，直至猜中该数字，显示“预测N次，你猜中了!”，其中N是用户输入数字的次数。



4.2  统计不同字符个数。用户从键盘输入一行字符，编写一个·程序，统计并输出其中英文字符、数字、空格和其他字符的个数。



4.3 最大公约数计算。从键盘接受两个整数，编程求这两个整数的最大公约数和最小公倍数.



4.4 猜数字游戏。改编4.1 ，随机数范围改为0-100.



4.5 猜数游戏续。当用户输入不是整数时，给出“输入内容必须是整数”的提示，并让用户重新输入。



4.6 羊车门问题。



4.7 使用异常处理改造实例1，使其能够接受并处理用户的任何输入。



