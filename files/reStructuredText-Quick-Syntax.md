**reStructuredText** 是扩展名为.rst的纯文本文件，含义为"重新构建的文本""，也被简称为：RST或reST；是Python编程语言的Docutils项目的一部分，Python Doc-SIG (Documentation Special Interest Group)。该项目类似于Java的JavaDoc或Perl的POD项目。 Docutils 能够从Python程序中提取注释和信息，格式化成程序文档。

.rst 文件是轻量级标记语言的一种，被设计为容易阅读和编写的纯文本，并且可以借助Docutils这样的程序进行文档处理，也可以转换为HTML或PDF等多种格式，或由Sphinx-Doc这样的程序转换为LaTex、man等更多格式。

本文语法来自[Quick reStructuredText](http://docutils.sourceforge.net/docs/user/rst/quickref.html)

# 行内样式

## 斜体

重点、解释文字

```
*重点(emphasis)通常显示为斜体*
`解释文字(interpreted text)通常显示为斜体`
```

*重点(emphasis)通常显示为斜体*


## 粗体

重点强调

```
**重点强调(strong emphasis)通常显示为粗体**
```
**重点强调(strong emphasis)通常显示为粗体**


## 等宽

```
``行内文本(inline literal)通常显示为等宽文本，空格可以保留，但是换行不可以。``
```

行内文本(inline literal)通常显示为等宽文本，空格可以保留，但是换行不可以。


# 章节标题

章节头部由下线(也可有上线)和包含标点的标题 组合创建, 其中下线要至少等于标准文本的长度。

可以表示标题的符号有 **=**、**-**、**`**、**:**、**'**、**"**、**~**、**^**、**_** 、__*__ 、**+**、 **#**、**<**、**>** 。

对于相同的符号，有上标是一级标题，没有上标是二级标题。

标题最多分六级，可以自由组合使用。

全加上上标或者是全不加上标，使用不同的 6 个符号的标题依次排列，则会依次生成的标题为H1-H6。

```
=========
一级标题
=========
二级标题
=========

一级标题
^^^^^^^^
二级标题
---------
三级标题
`````````
四级标题
:::::::::
五级标题
'''''''''
六级标题
""""""""
```

# 一级标题
## 二级标题

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
######六级标题

---

# 段落

段落是被空行分割的文字片段，左侧必须对齐（没有空格，或者有相同多的空格）。

缩进的段落被视为引文。


# 列表

## 符号列表(Bullet Lists)

符号列表可以使用 **-**、 __*__、**+** 来表示。

不同的符号结尾需要加上空行，下级列表需要有空格缩进。

```
- 符号列表1
- 符号列表2

  + 二级符号列表1

  - 二级符号列表2

  * 二级符号列表3

* 符号列表3

+ 符号列表4
```

- 符号列表1
- 符号列表2
  + 二级符号列表1
  - 二级符号列表2
  * 二级符号列表3
* 符号列表3
+ 符号列表4

## 枚举(顺序)列表(Enumerated Lists)

枚举列表算即顺序(序号)列表，可以使用不同的枚举序号来表示列表。

>**可以使用的枚举有：**
- 阿拉伯数字: 1, 2, 3, ... (无上限)。
- 大写字母: A-Z。
- 小写字母: a-z。
- 大写罗马数字: I, II, III, IV, ..., MMMMCMXCIX (4999)。
- 小写罗马数字: i, ii, iii, iv, ..., mmmmcmxcix (4999)。

可以为序号添加前缀和后缀，下面的是被允许的。

**.** 后缀: "1.", "A.", "a.", "I.", "i."。
**()** 包起来: "(1)", "(A)", "(a)", "(I)", "(i)"。
**)** 后缀: "1)", "A)", "a)", "I)", "i)"。

枚举列表可以结合 **#** 自动生成枚举序号。

```
1. 枚举列表1
#. 枚举列表2
#. 枚举列表3

(I) 枚举列表1
(#) 枚举列表2
(#) 枚举列表3

A) 枚举列表1
#) 枚举列表2
#) 枚举列表3
```

1. 枚举列表1
2. 枚举列表2
3. 枚举列表3

I. 枚举列表1
II. 枚举列表2
III. 枚举列表3

A. 枚举列表1
B. 枚举列表2
C. 枚举列表3


## 定义列表(Definition Lists)

定义列表可以理解为解释列表，即名词解释。

条目占一行，解释文本要有缩进；多层可根据缩进实现。

```
定义1
 这是定义1的内容

定义2
 定义2-1
  定义2-1内容

 定义2-2
  定义2-2内容
```

定义1

    这是定义1的内容  
定义2

    这是定义1的内容


## 字段列表(Field Lists)

```
:标题: reStructuredText语法说明

:作者:
 - Seay
 - Seay1
 - Seay2

:时间: 2016年06月21日

:概述: 这是一篇
 关于reStructuredText

 语法说明。
```

**标题:** reStructuredText语法说明  
**作者:**
 - Seay
 - Seay1
 - Seay2

**时间:**	2016年06月21日  
**概述:** 这是一篇 关于reStructuredText  
语法说明。


## 选项列表(Option Lists)

选项列表是一个类似两列的表格，左边是参数，右边是描述信息。当参数选项过长时，参数选项和描述信息各占一行。

选项与参数之间有一个空格，参数选项与描述信息之间至少有两个空格。

```
-a            command-line option "a"
-b file       options can have arguments
              and long descriptions
--long        options can be long also
--input=file  long options can also have
              arguments
/V            DOS/VMS-style options too
```

| 参数选项 | 描述信息 |
| ------- | ------- |
| -a | command-line option "a"|
| -b file | options can have arguments and long descriptions |
| --long | options can be long also |
| --input=file | long options can also have arguments |
| /V | DOS/VMS-style options too |

*由于格式问题，这里只是一个示例，实际上时没有上面的表头列和表格竖直线的。*

# 块(Blocks)

## 文字块(Literal Blocks)

文字块就是一段文字信息，在需要插入文本块的段落后面加上 **::**，接着一个空行，然后就是文字块了。

文字块不能定顶头写，要有缩进，结束标志是，新的一段文本贴开头，即没有缩进。

```
下面是文字块内容：
::

   这是一段文字块
   同样也是文字块
   还是文字块

这是新的一段。
```

下面是文字块内容：
```
这是一段文字块
同样也是文字块
还是文字块
```
这是新的一段。

## 行块(Line Blocks)

行块对于地址、诗句以及无装饰列表是非常有用的。行块是以 **|** 开头，每一个行块可以是多段文本。

**|** 前后各有一个空格。

```
下面是行块内容：
 | 这是一段行块内容
 | 这同样也是行块内容
   还是行块内容

这是新的一段。
```

下面是行块内容：

    这是一段行块内容  
    这同样也是行块内容 还是行块内容

这是新的一段。

## 块引用(Block Quotes)

块引用是通过缩进来实现的，引用块要在前面的段落基础上缩进。

通常引用结尾会加上出处(attribution)，出处的文字块开头是 **--**、**---** 、**—**，后面加上出处信息。

块引用可以使用空的注释 **..** 分隔上下的块引用。

注意在新的块和出处都要添加一个空行。

```
下面是引用的内容：

    “真的猛士，敢于直面惨淡的人生，敢于正视淋漓的鲜血。”

    --- 鲁迅

..

      “人生的意志和劳动将创造奇迹般的奇迹。”

      — 涅克拉索
```

下面是引用的内容：

    “真的猛士，敢于直面惨淡的人生，敢于正视淋漓的鲜血。”
    —鲁迅

    “人生的意志和劳动将创造奇迹般的奇迹。”
    —涅克拉索

## 文档测试块(Doctest Blocks)

文档测试块是交互式的Python会话，以 **>>>** 开始，一个空行结束。

```

```

# 表格(Tables)

reStructuredText提供两种表格：网格表（Grid Tables），简单表（Simple Tables）。

## 网格表(Grid Tables)

网格表中使用的符号有：**-**、**=**、**|**、**+**。

**-** 用来分隔行， **=** 用来分隔表头和表体行，**|** 用来分隔列，**+** 用来表示行和列相交的节点。

```
Grid table:

+------------+------------+-----------+
| Header 1   | Header 2   | Header 3  |
+============+============+===========+
| body row 1 | column 2   | column 3  |
+------------+------------+-----------+
| body row 2 | Cells may span columns.|
+------------+------------+-----------+
| body row 3 | Cells may  | - Cells   |
+------------+ span rows. | - contain |
| body row 4 |            | - blocks. |
+------------+------------+-----------+
```

效果请查看:[这里](http://docutils.sourceforge.net/docs/user/rst/quickref.html#tables)

## 简单表(Simple Tables)

简单表相对于网格表，少了 **|** 和 **+** 两个符号，只用 **-** 和 **=** 表示。

```
Simple table:

=====  =====  ======
   Inputs     Output
------------  ------
  A      B    A or B
=====  =====  ======
False  False  False
True   False  True
False  True   True
True   True   True
=====  =====  ======
```

效果请查看:[这里](http://docutils.sourceforge.net/docs/user/rst/quickref.html#tables)


# 分隔符

分隔符就是一条水平的横线，是由 4 个 **-** 或者更多组成，需要添加换行。

```
上面部分

------------

下面部分
```

上面部分

---

下面部分


# 超链接

介绍各类带有链接性质的超链接

## 自动超链接

reStructuredText会自动将网址生成超链接。

```
https://github.com/SeayXu/
```

[https://github.com/SeayXu/][github]


## 外部超链接(External Hyperlink)

引用/参考(reference)，是简单的形式，只能是一个词语，引用的文字不能带有空格。

```
这篇文章来自我的Github,请参考 reference_。

.. _reference: https://github.com/SeayXu/
```

引用/参考(reference)，行内形式，引用的文字可以带有空格或者符号。

```
这篇文章来自我的Github,请参考 `SeayXu <https://github.com/SeayXu/>`_。
```

这篇文章来自我的Github,请参考 [SeayXu][github]。


## 内部超链接|锚点(Internal Hyperlink)

```
更多信息参考 引用文档_

这里是其他内容

.. _引用文档:

这是引用部分的内容
```

更多信息参考 [引用文档](#id1)

这里是其他内容

<h6 id="id1"></h6>

这是引用部分的内容


## 匿名超链接(Anonymous hyperlink)

词组(短语)引用/参考(phrase reference)，引用的文字可以带有空格或者符号，需要使用反引号引起来。

```
这篇文章参考的是：`Quick reStructuredText`__。

.. __: http://docutils.sourceforge.net/docs/user/rst/quickref.html
```
这篇文章来自我的Github,请参考 [Quick reStructuredText][rstqs]。


## 间接超链接(Indirect Hyperlink)

间接超链接是基于匿名链接的基础上的，就是将匿名链接地址换成了外部引用名_。

```
SeayXu_ 是 `我的 GitHub 用户名`__。

.. _SeayXu: https://github.com/SeayXu/

__ SeayXu_
```
[SeayXu][github] 是 [我的 GitHub 用户名][github]。


## 隐式超链接(Implicit Hyperlink)

小节标题、脚注和引用参考会自动生成超链接地址，使用小节标题、脚注或引用参考名称作为超链接名称就可以生成隐式链接。

```
第一节 介绍
===========

其他内容...

隐式链接到 `第一节 介绍`_，即可生成超链接。
```

<h6 id="id2">第一节 介绍</h6>

其他内容...

隐式链接到 [第一节 介绍](#id2)，即可生成超链接。


## 替换引用(Substitution Reference)

替换引用就是用定义的指令替换对应的文字或图片，和内置指令(inline directives)类似。

```
这是 |logo| github的Logo，我的github用户名是:|name|。

.. |logo| image:: https://help.github.com/assets/images/site/favicon.ico
.. |name| replace:: SeayXu
```

这是 ![][logo] GitHub的Logo，我的github用户名是:SeayXu。

## 脚注引用(Footnote Reference)

脚注引用，有这几个方式：有手工序号(标记序号123之类)、自动序号(填入#号会自动填充序号)、自动符号(填入*会自动生成符号)。

手工序号可以和#结合使用，会自动延续手工的序号。


**#** 表示的方法可以在后面加上一个名称，这个名称就会生成一个链接。

```
脚注引用一 [1]_
脚注引用二 [#]_
脚注引用三 [#链接]_
脚注引用四 [*]_
脚注引用五 [*]_
脚注引用六 [*]_

.. [1] 脚注内容一
.. [2] 脚注内容二
.. [#] 脚注内容三
.. [#链接] 脚注内容四 链接_
.. [*] 脚注内容五
.. [*] 脚注内容六
.. [*] 脚注内容七
```

脚注引用一 [[1]](#id3)<a id="id9"></a>
脚注引用二 [[3]](#id4)<a id="id10"></a>
脚注引用三 [[4]](#id5)<a id="id11"></a>
脚注引用四 [[*]](#id6)<a id="id12"></a>
脚注引用五 [[†]](#id7)<a id="id13"></a>
脚注引用六 [[‡]](#id8)<a id="id14"></a>

[[1]](#id9)<a id="id3"></a> 脚注内容一  
[2]  脚注内容二  
[[3]](#id10)<a id="id4"></a> 脚注内容三  
[[4]](#id11)<a id="id5"></a> 脚注内容四 [链接](#id11)  
[[*]](#id12)<a id="id6"></a> 脚注内容五  
[[†]](#id13)<a id="id7"></a> 脚注内容六  
[[‡]](#id14)<a id="id8"></a> 脚注内容七  

## 引用参考(Citation Reference)

引用参考与上面的脚注有点类似。

```
引用参考的内容通常放在页面结尾处，比如 [One]_，Two_

.. [One] 参考引用一
.. [Two] 参考引用二
```

引用参考的内容通常放在页面结尾处，比如 [[One]](#15)<a id="id17"></a>，[Two](#16)

>[[One]](#17)<a id="id15"></a> 参考引用一
>[Two]<a id="id16"></a> 参考引用二


# 注释(Comments)

注释以 **..** 开头，后面接注释内容即可，可以是多行内容，多行时每行开头要加一个空格。

```
..
 我是注释内容
 你们看不到我
```

关于 [指令(Directives)](./reStructuredText-Directives-Syntax.md)，在下一篇中专门做语法说明。

[github]:https://github.com/SeayXu/
[rstqs]:http://docutils.sourceforge.net/docs/user/rst/quickref.html
[logo]:https://help.github.com/assets/images/site/favicon.ico
