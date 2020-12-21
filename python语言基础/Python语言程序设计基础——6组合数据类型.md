# Python语言程序设计基础

# 第6章 组合数据类型

------

[TOC]

------

## 组合数据类型概述

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201212215013.png)

组合数据类型可以分为3类：序列类型、集合类型和映射类型。

序列类型是一个元素向量，元素之间存在先后关系，通过序号访问，元素之间不排他。

集合序列是一个元素集合，元素之间无序，相同元素在集合中唯一存在。

映射类型是“建-值”数据项的组合，每个元素是一个键值对，表示为(key,value)



### 序列类型



序列类型是一维元素向量，元素之间存在先后关系，通过序号访问。

当需要访问序列中某个特定值时，只需通过下标标出即可。

1. 字符串：字符串可以看出单一字符的有序组合，属于序列类型
2. 元组：元组是包含0个或多个数据项的不可变序列类型。元组生成后是固定的，其中任何数据项不能替换或删除。
3. 列表：列表是一个可以修改数据项的序列类型



无论是哪种数类型，只要它是序列类型，都可以使用相同的序列体系，及正向递增序列和反向递减序列。

**序列类型的通用操作符和函数 12个**

| 操作符             | 描述                                                     |
| ------------------ | -------------------------------------------------------- |
| x in s             | 如果x是s的元素，返回True，否则返回False                  |
| x not in s         | 如果x不是s的元素，返回True，否则返回False                |
| s + t              | 连接s和t                                                 |
| s * n              | 将序列s复制n次                                           |
| s[i]               | 索引，返回序列的第i个元素                                |
| s[i:j]             | 分片，返回序列s第i到第j个元素的子序列（不包含第j个元素） |
| s[i:j:k]           | 步骤分片，返回序列s第i到第j个元素以k为步数的子序列       |
| len(s)             | 序列s的元素个数(长度）                                   |
| min(s)             | 序列s的最小元素                                          |
| max(s)             | 序列s的最大元素                                          |
| s.indec(x[,i[,j]]) | 序列s中从i开始到j位置中第一次出现元素x的位置             |
| s.count()          | 序列s中出现x的总次数                                     |



元组 是序列中比较特殊的类型，因为它一旦创建就不能被修改。元组类型在表达固定数据项、函数多返回值、多变量同步赋值、循环遍历等情况下十分有用。

Python中元组采用逗号和圆括号来表示。生成元组只需使用逗号将元素隔离开即可，也可以增加圆括号。

一个元组可以作为另一个元组的元素，可以采用多级索引获取信息。

```python
creature = "cat" ,"dog","tiger","human"
print(creature)
color = ("red","0x011100","blue",creature)
print(color)
print(color[2])
print(color[-1][2])
```

元组除了用于表达固定数据项外，还常用于如下3中情况：函数多返回值、多变量同步赋值、循环遍历。

```python
#函数多返回值
def  func(x):
    return x, x**3 
#多变量同步赋值
a, b = 'dag' , 'tiger'
#多变量同步赋值，括号可以省略
a, b  = (b,a)
# 求多个坐标到远点的距离1
#循环遍历
import math
for x , y in ((1,0),(2,5),(3,8)):
    print(math.hypot(x,y))
```



### 集合类型

集合类型与数学中集合的概念一致，即包含0个或多个数据项的无序组合。

集合中的元素不可重复，元素类型只能是固定数据类型，例如整数、浮点数、字符串、元组等，列表、字典和集合类型本身都是可变数据类型，不能作为集合元素。Python编译器界定固定数据类型与否主要考察类型是否能够。能够进行哈希运算的类型都可以作为集合元素。

Python提供了一种同名的具体数据类型——集合Set

由于集合是无序组合，他没有索引和位置的概念，不能分片，集合中元素可以动态增加或删除。

集合用大括号{}表示，可以用赋值语句生成一个集合，

```python
S = {425,424, (10,'CS'),'BIT'}
print(S)
T = { 425, "BIT",(10,"CS"),424,425,"BIT"}
print(T)
```

由于集合元素是无序的，集合的打印效果与定义顺序可以不一致。

由于集合元素独一无二，使用集合类型能够过滤重复元素。

set(x)函数可以生成集合，输入的参数可以是任何组合数据类型，返回结果与是一个无重复且排序任意的集合。

![](https://zuti.oss-cn-qingdao.aliyuncs.com/img/20201213081912.png)

**集合类型的操作符 共10个** 

| 操作符                                    | 描述                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| S- T  或 S.differencr(T)                  | 差集运算，返回一个新集合，包括在集合S中但不在集合T中的元素   |
| S -= T 或 S.difference_update(T)          | 更新集合S，包括在集合S中但不在集合T中的元素                  |
| S & T 或 S.intersection(T)                | 交集运算，返回一个新集合，包括同时在集合S和T中的元素         |
| S & = T 或S.intersection_update(T)        | 更新集合S，包括同时在集合S和T中的元素                        |
| S ^ T 或 s.symmetric_difference(T)        | 补集运算，返回一个新集合，包括集合S和T的元素，但不包含同时在其中的元素 |
| S= ^T 或 s.symmetric_difference_update(T) | 更新集合S，包括集合S和T的元素，但不包含同时在其中的元素      |
| S \|T 或 S.union(T)                       | 交集运算，返回一个新集合，包括集合S和T中的所有元素           |
| S\|=T 或S.update(T)                       | 更新结合S，包括集合S和T中的所有元素                          |
| S<=T 或 S.isubset(T)                      | 如果S与T相同或S是T的子集，返回True,否则返回False;可以用S<T判断S是否是T的真子集 |
| S>=T 或 S.isuperset(T)                    | 如果S与T相同或S是T的超集，返回True,否则返回False;可以用S<T判断S是否是T的真超集 |

**集合类型的操作函数或方法 共10个**

| 操作函数        | 描述                                                         |
| --------------- | ------------------------------------------------------------ |
| S.add(x)        | 如果数据项不在集合S中，将x增加到s                            |
| S.clear()       | 移除S中的所有数据项                                          |
| S.copy()        | 返回集合S的一个副本                                          |
| S.pop()         | 随即返回集合S的一个元素，如果集合S为空，产生KeyError异常     |
| S.discard(x)    | 如果x 在集合S中，移除该元素；如果x不在集合S中，不报错        |
| S.remove(x)     | 如果x 在集合S中，移除该元素；如果x不在集合S中，产生KeyError异常 |
| S.isdisjoint(T) | 如果集合S与T没有相同元素，返回True                           |
| len(S)          | 返回集合S的元素个数                                          |
| x in S          | 如果x是S的元素，返回True，否则返回False                      |
| x not in S      | 如果x不是S的元素，返回True，否则返回False                    |

集合类型主要用于3个场景：成员关系测试，元素去重和删除数据项

```python
#成员关系测试
print("BIT" in {"PYTHON","BIT",123,"GOOD"})

#元素去重
tup = "PYTHON" ,"BIT", 123,"GOOD" , 123
print(tup)
print(set(tup))

#去重同时删除数据项
newtup  = tuple( set(tup) - {"PYTHON"})
print(newtup)
```

### **映射类型**



## 列表类型和操作

列表是包含0个或多个对象引用的有序序列。列表的长度和内容是可变的。列表没有长度限制。

列表的比较实际上是单个数据项的逐个比较

列表用中括号[]表示，也可以通过list()函数将元组或字符串转化为列表

> 列表和数组的比较：
>
> 1 数组需预先分配大小，列表不需要
>
> 2 数组要求元素类型一致，列表不需要

将列表赋值给另一个列表不会产生新的列表对象，只会产生一个对象的新的引用

**列表类型特有的函数 14个**

| 函数                   | 描述                                                |
| ---------------------- | --------------------------------------------------- |
| ls[i]=x                | 替换列表ls第i数据项为x                              |
| ls[i:j]=lt             | 用列表lt替换列表ls第i到第j项数据（不含第j项，下同） |
| ls[i:j:k]=lt           | 用列表lt替换列表ls第i到第j项以步长为k的步数的数项   |
| del ls[i:j]            | 删除列表ls第i到第j项数据，等价于ls[i:j]=[]          |
| ls+=lt 或ls.extend(lt) | 将列表lt增加到列表ls中                              |
| ls *= n                | 更新列表ls,将其元素重复n次                          |
| ls.append(x)           | 在列表最后增加一个元素x                             |
| ls.clear()             | 删除ls中的所有元素                                  |
| ls.copy()              | 生成一个新列表，复制ls中的所有元素                  |
| ls.insert(i,x)         | 在列表ls的第i项元素取出并删除该元素                 |
| ls.pop(i)              | 在列表ls的第i项元素取出并删除该元素                 |
| ls.remove(x)           | 将列表中出现的第一个元素x删除                       |
| ls.reverse(x)          | 列表ls中的元素反转                                  |



思考与练习

6.4 列表ls = 【2,4,7,16】，请对列表按着升序和降序的方式分别排列。提示：请使用Python内置函数

```python
ls = [2,4,7,16]
print(sorted(ls))
print(sorted(ls,reverse=True))
```

6.5 列表ls1 = 【30,1,2,0】 ls2=[1,21,133]，请比较两个列表

```python
ls1 = [30,1,2,0]
ls2 = [1,21,133]
print(ls1>ls2)
```

6.6 列表ls1=[1,43] ls2=ls1 ,ls[0]=22 请计算并思考两个列表的运算结果、

```python
ls1 = [1,43]
ls2 =ls1 
ls1[0]=22
print(ls1)
print(ls2)
```

ls2 是 ls1的引用，也就是说两个变量名对应着同一个地址

6.7 列表ls=【[2,3,7],【[3,5],25】,[0,9]】len(ls)的值是多少？

 3  len只统计第一层







## 实例9：基本数据统计量



IPO描述

> 输入：从用户输入、文件、网络等途径获取一组数据
>
> 处理：适当的数据结构和算法
>
> 输出：平均值、标准差和中位数
>
>  由于问题不限制用户输入数据的最大个数，所以使用列表作为承载和存储数据的数据类型

```python
# 基本统计值计算
from math import sqrt
#获取用户输入
def getNum():
    nums = []
    iNumStr = input("请输入数字(直接输入回车退出)：")
    while iNumStr != "":
        nums.append(eval(iNumStr))
        iNumStr = input("请输入数字（直接输入回车退出)")
    return nums

#计算平均值
def mean(numbers):
    s = 0.0
    for num in  numbers:
        s = s+ num
    return s / len(numbers)

#计算方差
def dev(numbers ,mean):
    sdev = 0.0
    for num in numbers:
        sdev = sdev +(num-mean)**2
    return sqrt(sdev/(len(numbers)-1))

#计算中位数
def median(numbers):
    sorted(numbers)
    size = len(numbers)
    if size % 2 ==0:
        med  = (numbers[size//2-1] + numbers[size//2])/2
    else:
        med = numbers[size//2]
    return med

#主体函数
n = getNum()
m = mean(n)
print(f'平均值{m},方差{dev(n,m):.2},中位数{median(n)}')
```

列表在实现基本数据统计时发挥了重要作用，主要表现在三个方面:

1. 列表是一个动态长度的数据结构，可以根据需求增加或减少元素

2. 列表的一系列方法或操作符为计算提供了简单的元素运算手段

3. 列表提供了对每个元素的简单访问方式及所有元素的遍历方式

   

## 字典类型和操作



Python语言中的字典可以通过大括号{}建立，

> 直接使用大括号生成一个空的字典，而不是集合。生成空集合需要使用函数set()

```python
{<键1>:<值1>，<键2>:<值3>，。。。。。,<键n>:<值n>}
```

键和值通过冒号连接，不同键值对通过逗号隔开，

键值对之间没有顺序且不能重复

字典最主要的用法是查找与特定键相对应的值，通过索引符号来实现

一般来说，字典中键值对的访问模式采用中括号形式：

```
<值> = <字典变量> [<键>]
```

字典中对某个键值的修改可以通过中括号的访问与赋值实现。

```python
Dcountry ={"中国":"北京","美国":"华盛顿","法国":"巴黎"}
print(Dcountry)
print(Dcountry["美国"])
Dcountry["英国"]="伦敦"
print(Dcountry)
Dcountry["中国"]="大北京"
print(Dcountry)
Dp = {}
Dp["2^10"]=1024
print(Dp)
```

**字典类型的函数 共9 个**

| 函数                       | 描述                                               |
| -------------------------- | -------------------------------------------------- |
| ~<d>.keys()~               | 返回所有的键信息                                   |
| ~<d>.values~               | 返回所有的值信息                                   |
| ~<d>.items~                | 返回所有的键值对                                   |
| ~<d>.get(<key>,<default>)~ | 键存在则返回响应值，否则返回默认值                 |
| ~<d>.pop(<key>,<default>)~ | 键存在则返回相应值，同时删除键值对，否则返回默认值 |
| ~<d>.popitem()~            | 随机从字典中取出一个键值对，以元组形式返回         |
| ~<d>.clear~                | 删除所有的键值对                                   |
| ~del<d>[<key>]~            | 删除字典中某一个键值对                             |
| ~<key>in<d>~               | 如果键在字典中则返回True,否则返回False             |

如果希望keys(),values(),和items()方法返回列表类型，可以通过list()函数将返回值转换为列表

字典可以通过for-in 语句对其元素进行遍历，基本语法结构如下：

```python
for <变量名> in <字典名>:
	<语句块>
```

由于键值对中的键相当于索引，因此for循环返回的变量名是字典的索引值。如果需要获得键对应的值，可以在语句块中通过get()方法获得。

```python
Dcountry ={"中国":"北京","美国":"华盛顿","法国":"巴黎"}
print(Dcountry.keys())
print(list(Dcountry.values()))
print(Dcountry.items())
#只对键进行判断
print("中国"in Dcountry)
print(Dcountry.get("美国"))
for key in Dcountry:
    print(key,end="")
    print(Dcountry.get(key))
```

## 模块4 jieba库的使用

jieba是Python中一个重要的第三方中文分词函数库。jieba库的分词原理是利用一个中文词库，将待分词的内容与分词库进行比较，通过图结构和动态规划方法找到最大概率的词组。

jieba库支持3中分词模式

1. 精确模式，将句子最精确地切开，适合文本分析；
2. 全模式：把句子中所有可以成词的词语都扫描出来
3. 搜索引擎模式：在精确模式的基础上，对长词再次切分，提高召回率

**jieba库常用的分词函数 共7个**

| 函数                       | 描述                                         |
| -------------------------- | -------------------------------------------- |
| jieba.cut(s)               | 精确模式，返回一个可迭代的数据类型           |
| jieba.cut(s,cut_all=True)  | 全模式，输出文本s中所有可能的单词            |
| jieba.cut_for_search(s)    | 搜索引擎模式，适合搜索引擎建立索引的分词结果 |
| jieba.lcut                 | 精确模式，返回一个列表类型                   |
| jieba.lcut(s,cut_all=True) | 全模式，返回一个列表类型                     |
| jieba.lcut_for_search(s)   | 搜索引擎模式，返回一个列表类型               |
| jieba.add_word(w)          | 向分词词典中增加新词                         |

- jieba.lcut() 函返回精确模式，输出的分词能够完整且不多余地组成原始文本
- jieba.lcut(,True)函数返回全模式，输出原始文本中可能产生的所有分词，冗余性最大
- jieba.lcut_for_search()函数返回搜索引擎模式，首相执行精确模式，然后再对长词进一步切分

由于列表类型灵活方便且通用，建议读者使用上述3个能返回列表类型的分词函数

默认情况下，jieba.cut()等6个分词函数能够较高概率识别自定义的新词，比如名字或缩写。对于无法识别的分词，也可以通过jieba.add_word()函数向分词库中添加。

```python
import jieba 
print(jieba.lcut("中华人民共和国是一个伟大的国家"))
print(jieba.lcut("中华人民共和国是一个伟大的国家",cut_all=True))
print(jieba.lcut_for_search("中华人民共和国是一个伟大的国家"))
print(jieba.lcut("习大大盼望有更好的教育"))
jieba.add_word("习大大")
print(jieba.lcut("习大大盼望有更好的教育"))
```



## 实例10 ：文本词频统计

采用字典来解决词频统计问题

> 输入：从文件中读取一篇文章
>
> 处理：采用字典数据结构统计词语出现频率
>
> 输出：文章中最常出现的10个单词及出现次数



### Hamlet英文词频统计

1. 文本文件的获取

   网络资源 txt文本格式

2. 分解并提取文章的单词

   > 问题一：同一个单词会有大小写不同形式，但是计数不能区别大小写
   >
   > 解决：将字母转为小写，排除大小写干扰 lower()
   >
   > 问题二：标点符号，特殊字符的处理
   >
   > 解决：替换为空格 replace()

3. 单词的计数

   > 使用字典类型，键是单词，值为出现的次数。
   >
   > 当遇到一个新词时，需要在字典中新建键值对；已出现过，计数加一
   >
   > ```python
   > counts={}
   > if word in counts:
   >     counts[word] = counts[word]+1
   > else:
   >     counts[word]=1
   > ```
   >
   > 更简洁的代码
   >
   > ```python
   > counts[word] = counts.get(word,0)+1
   > ```
   >
   > counts.get(word,0)方法表示：如果word在counts中，则返回word对应的值，否则返回0

4. 对单词统计量的排序

   > 字典没有顺序，需要将其转为有顺序的列表类型，
   >
   > 再用sort()方法和lambda函数配合实现根据次数排序

   

   

```python
#Hamlet英文词频统计分析
#读取文本，并将特殊字符转化为空格
def getText():
    txt = open("hamlet.txt","r").read()
    #将字符转为小写
    txt = txt.lower()
    #将文本中特殊字符替换为空格
    for ch in '!"#$%&()*+-/,.:;<>=?@[\\]^_{|}~`':
        txt = txt.replace(ch," ")
    return txt
hamletTxt = getText()
#根据空格对单词进行分割
words = hamletTxt.split()
#统计，计数单词
counts ={}
for word in words:
    counts[word] = counts.get(word,0)+1
#将统计结果转为list
items = list(counts.items())
#根据次数进行排序
items.sort(key=lambda x:x[1], reverse=True)
#输出结果
for i in range(800):
    if(i>500):
        word , count = items[i]
        print(f'{word:<10}  {count:>5}' )
```

从结果可以看出高频单词大多数是冠词，代词，联结词等语法型词汇，并不能代表文章的含义。

进一步，可以采用集合类型构建一个排除词汇库excludes，在输出结果中排除这个词汇库的内容

```python
#Hamlet英文词频统计分析
#读取文本，并将特殊字符转化为空格
#排除语法词汇库,
excludes = {"a","the",
            "he","she","you","i","we","they","me","him","us","them","his","her","my","your","our",
            "this","that","it","there","what","how",
            "but","and","or","so","not","no","if","all",
            "is","be","are","was",
            "in","to","of","with","for","as","on","by","from","at",
            "have","do","did","will","would",
            "now",
            "more","most"}
def getText():
    txt = open("hamlet.txt","r").read()
    #将字符转为小写
    txt = txt.lower()
    #将文本中特殊字符替换为空格
    for ch in '!"#$%&()*+-/,.:;<>=?@[\\]^_{|}~`':
        txt = txt.replace(ch," ")
    return txt
hamletTxt = getText()
#根据空格对单词进行分割
words = hamletTxt.split()
#统计，计数单词
counts ={}
for word in words:
    counts[word] = counts.get(word,0)+1
#排除语法词汇
for word in excludes:
    del(counts[word])
    
#将统计结果转为list
items = list(counts.items())
#根据次数进行排序
items.sort(key=lambda x:x[1], reverse=True)
#输出结果
for i in range(10):
    word , count = items[i]
    print(f'{word:<10}  {count:>5}' )
```



### 《三国演义》人物出场统计

```
# 三国演义人物出场次统计
import jieba
#排除无关词

excludes = {"却说","二人","不可","不能","如此","如何"} 
guan={"将军","丞相","主公","军士","陛下","都督","后主"}
location={"荆州","东吴","汉中","江东","徐州","成都","洛阳","襄阳","祁山","樊城"}

#
txt = open("threekingdoms.txt","r",encoding='utf-8').read()
words = jieba.lcut(txt)
counts={}

for word in words:
    if len(word) ==1 : #排除单个字符的分词结果
        continue
    elif word == "诸葛亮" or word == "孔明曰":
        rword  = "孔明"
    elif word == "关公" or word == "云长":
        rword  = "关羽"
    elif word == "玄德" or word == "玄德曰":
        rword  = "刘备"
    elif word == "孟德" :
        rword  = "曹操"
    else:
        rword = word
    counts[rword] = counts.get(rword,0)+1
#排除无关词汇
for word in excludes:
    del(counts[word])
for word in guan:
    del(counts[word])
for word in location:
    del(counts[word])
    
items = list(counts.items())
items.sort(key=lambda x:x[1],reverse=True)
for i in range(200):
    word , count = items[i]
    print(f'{word:<10}  {count:>5}')
```

lambd x;

 x[1]

定义了一个匿名函数，返回列表x的第二项x[1]



## 实例11 Python之禅

