# string 模块

1. 大小写转换

   - upper() 注意是通过生成新的字符串而不是更改原来字符串
   - lower()
   - title()          将给定的字符串中所有单词的首字母大写，其他全部小写
   - capitalize()将给定的字符串中首字母大写，其他小写
   - swapcase()将原字符串中的大写改为小写，小写再改为大写

2. is判断函数

   - isupper()	判断给定的字符串是否全为大写
   - islower()     判断给定的字符串是否全为小写
   - istitle()        判断给定的字符串是否符合title()
   - isalpha()    判断给定的字符串是否全为字母
   - isalnum()   判断给定的字符串是否只含有数字与字母
   - isdecimal() 判断给定字符串是否全为数字

3. 字符串填充

   - 参数：扩充的长度  width  当字符串比width小时才会扩充，当字符串大于长度时返回字符串本身；

     ​			扩充的字符  str必须是单个的字符

   - 扩充的位置  

     -  居中center(width，str) 原来的字符串将会在中间，扩充物出现在两边
     -  居左 ljust(width，str)，l为lef的缩写，源字符串在左边，填充物出现在字符串的右边
     - 居右 rjust(width), r为right的缩写，源字符串在右边，填充物出现在字符串的左边

   - zfill(width)                      

4. 子字符串搜索

   - count(sub[, start[, end]])主要对指定字符串搜索是否具有给定的子字符串sub,若具有则返回出现次数。start与end代表搜索边界，若无写则代表全字符串搜索

   - 字符串开始与结尾判断  

     - startswith(prefix[, start[, end]])   
     - endswith(suffix[, start[, end]])
     - 判断函数的开始，或者末尾的字符串是否为指定字符串可以给字符串加边界，若无则为全字符串搜索.两个函数都属于判断函数，返回结果为True与False

   - find(sub[, start[, end]]) 返回第一个子字符串的位置信息，若无则为-1
     rfind(sub[, start[, end]])返回最右边的第一个子字符串的位置信息，若无则为-1
     index(sub[, start[, end]]) 返回第一个子字符串的位置信息，若无则为报错
     rindex(sub[, start[, end]])返回最右边的第一个子字符串的位置信息，若无则报错

     从传参可以看出，查询位置函数也可以限定边界，使用方法同上函数

5. 字符串替换

   - replace(old, new[, count])：将搜索到的字符串改为新字符串

     作为替代函数，旧的字符串与新的字符串是必须输入的，count是可选择输入的参数，代表更改个数。

   - expandtabs(N) :将\t 改为一定数量的空格

6. 字符串分割

   - partition() 和 rpartition()

      partition(sep)对给定字符串进行切割，切割成三部分。首先搜索到字符串sep，将sep之前的部分为一部分，sep本身作为一部分，剩下作为一部分

   - split(sep=None, maxsplit=-1) 和 rsplit(sep=None, maxsplit=-1) split()函数传参两种 

     sep为切割，默认为空格，maxsplit为切割次数，给值-1或者none，将会从左到右每一个sep切割一次。

7. 字符串添加

   - join()    将可迭代数据用字符串连接起来 ，首先理解什么是可迭代数据，简单理解就是字符串string、列表list、元组tuple、字典dict、集合set。而且每个参与迭代的元素必须是字符串类型，不能包含数字或其他类型。

8. 字符串修剪

   - strip([chars]) lstrip([chars]) rstrip([chars])

     strip()是为移除指定字符串char，如果没传入参数则为移除空格、制表符、换行符。lstrip()中 l为left缩写，函数表示从左到右遍历，rstrip()中 r为right缩写，函数表示从右边开始遍历。

     注意移除为到非char截止