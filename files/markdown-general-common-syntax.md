# 前言
**Markdown** 是一种轻量级的 **标记语言**，语法简洁明了、学习容易，还具有其他很多优点，目前被越来越多的人用来写作使用。

>Markdown具有一系列衍生版本，用于扩展Markdown的功能（如表格、脚注、内嵌HTML等等），这些功能原初的Markdown尚不具备，它们能让Markdown转换成更多的格式，例如LaTeX，Docbook。Markdown增强版中比较有名的有Markdown Extra、MultiMarkdown、 Maruku等。这些衍生版本要么基于工具，如Pandoc；要么基于网站，如GitHub和Wikipedia，在语法上基本兼容，但在一些语法和渲染效果上有改动。

由于一些扩展只在特定的环境中才能实现，所以这里介绍的是通用的常用语法说明。

# 语法

下面就是常用的Markdown语法内容，以标准Markdown语法为依据，可能这里有一些差异，请以语法为准。

## 标题
标题分为6级，对应HTML标签的h1~h6。**#**越多，字体越小。

```
# H1标题
## H2标题
### H3标题
#### H4标题
##### H5标题
###### H6标题
```
# H1标题
## H2标题
### H3标题
#### H4标题
##### H5标题
###### H6标题

---

## 分隔符
分隔符就是一条横线。
```
---
```
---

## 文本样式

### 斜体
```
* 斜体文本 *
_ 斜体文本 _
```
*斜体文本*  _斜体文本_

### 粗体
加粗就是是文字为粗体显示，可以使用下面两中方式表示：
```
** 粗体文本 **
__ 粗体文本 __
```

** 粗体文本 **

__粗体文本__

### 斜粗体
```
*** 斜粗体文本 *** *__ 斜粗体文本 __*
_** 斜粗体文本 **_ ___ 斜粗体文本 ___
```
*** 斜粗体文本 *** *__ 斜粗体文本 __*

_** 斜粗体文本 **_ ___ 斜粗体文本 ___

### 删除线
文字有一条删除线的效果
```
~~ 删除效果 ~~
```
~~删除效果~~

### 高亮
文字用醒目的高亮显示
```
这是` 高亮文本 `效果。
```
这是` 高亮文本 `效果。 

## 代码块
代码块就是将源码直接进行展示，可在开始的** ``` **后面加上代码语种名称。
```
`` `  javascript
var str = "hello world!";
alert(str);
`` `
```
_为了显示，上面给出的**  ``` **加了一个空格。_

``` javascript
var str = "hello world!";
alert(str);
```
上面就是效果


## 图片
图片展示
```
方式1：
![文本内容](https://help.github.com/assets/images/site/favicon.ico "logo")
方式2：
![文本内容][img]
[img]:https://help.github.com/assets/images/site/favicon.ico "logo"
```
方式1：
![文本内容](https://help.github.com/assets/images/site/favicon.ico "logo")
方式2：
![文本内容][img]
[img]:https://help.github.com/assets/images/site/favicon.ico "logo"

<h6 id="url-more">说明：</h6>

URL后面的内容是鼠标hover提示文本，可以省略，省略时就没有鼠标hover提示文本效果。

推荐使用方式2，当一个链接在文中多次出现的时候，就会体现出其优点了。

另外，后面的提示文本除了使用 **"**提示文本**"** 外，还可以是 **'**提示文本**'** 和 **(**提示文本**)** 。
```
[id]:URL "鼠标hover提示文本"
[id]:URL '鼠标hover提示文本'
[id]:URL (鼠标hover提示文本)
```

## 链接

链接根据链接目标可分为站内站外链接，按照类型可分为文本链接和图片链接。
综上所述，可分为以下三种：

### 文本链接
给文本信息添加超链接
```
1.<https://github.com/SeayXu>
2.[文本链接](https://github.com/SeayXu "SeayXu")
3.[文本链接][id]
[id]:https://github.com/SeayXu "SeayXu"
```
1.<https://github.com/SeayXu>
2.[文本链接](https://github.com/SeayXu "SeayXu")
3.[文本链接][id]
[id]:https://github.com/SeayXu "SeayXu"

链接URL相关说明和图片一样，[请查看](#url-more)

**特例：**
当链接的文本内容和链接Id相同的时候，可以不用写链接后面的Id。
```
[SeayXu][]
[SeayXu]: https://github.com/SeayXu "Seay"
```

[SeayXu][]
[SeayXu]: https://github.com/SeayXu "Seay"

### 图片链接
给图片加上超链接
```
方式1：
[![Github](https://help.github.com/assets/images/site/favicon.ico "Seay")](https://github.com/SeayXu  "SeayXu")
方式2：
[![Github][img-url]][link-url]
[link-url]:https://github.com/SeayXu "SeayXu"
[img-url]:https://help.github.com/assets/images/site/favicon.ico "Seay"
```
方式1：
[![Github](https://help.github.com/assets/images/site/favicon.ico "Seay")](https://github.com/SeayXu  "SeayXu")
方式2：
[![Github][github-img]][github-url]

>提示：由于各个Markdown解析不同，所以显示的提示文本有可能也不太一样。

### 锚点
锚点其实与文本链接和图片链接用法是一样的，只不过是在本页面内，需要稍微改动下。

**设置锚点链接目标：**
```
<h6 id="url-more">说明：</h6>
```

**添加锚点：**
```
[锚点](#url-more "anchor alt text")
[锚点][anchor]
[anchor]:#url-more "anchor alt text"
```
[锚点](#url-more "anchor alt text")
[锚点][anchor]
[anchor]:#url-more "anchor alt text"

>说明：相对于文本链接和图片链接，主要是添加了锚点链接目标这一操作，使用语法跟文本链接和图片链接一样。

## 列表
列表分为有序和无序两种。

### 无序列表
无序列表有三种表示方法：** * **、** + **和** - **。
>下级在上级基础上前面多加两个空格，符号与内容直接有一个空格。

无序列表1：
```
* 一级条目1
* 一级条目2
  * 二级条目1
  * 二级条目2
    * 三级条目1
    * 三级条目2
    * 三级条目3
  * 二级条目3
* 一级条目3
```
* 一级条目1
* 一级条目2
  * 二级条目1
  * 二级条目2
    * 三级条目1
    * 三级条目2
    * 三级条目3
  * 二级条目3
* 一级条目3

在这里只演示一种，另外两种就是把** * **分别换成 ** + **和** - **。

### 有序列表
有序列表与无序列表类似，只不是是将前面的符号换成数字而已。
```
1. 一级条目1
2. 一级条目2
  1. 二级条目1
  * 二级条目2
    * 三级条目1
    + 三级条目2
    - 三级条目3
  - 二级条目3
2. 一级条目3
```

1. 一级条目1
2. 一级条目2
  1. 二级条目1
  * 二级条目2
    * 三级条目1
    + 三级条目2
    - 三级条目3
  - 二级条目3
2. 一级条目3

**说明：**
>1. 有序列表有自动纠错功能，当序号输入错误时，会自动更正显示序号。
>2. 有序列表可结合无序列表，只在第一个条目输入序号后，同级条目会自动编号。

## 引用
引用内容可以嵌套引用和使用其他语法，在引用内容后面空一行就表示引用结束。
```
>这是一段包含**加粗**的 _斜体_ 和 _**斜粗体**_ 并带有`高亮`显示的一段文本来自[我的Github](https://github.com/SeayXu "SeayXu")。
我是图片：
![github logo][github-img]
[github-url]:https://github.com/SeayXu "SeayXu"
```
>这是一段包含**加粗**的 _斜体_ 和 _**斜粗体**_ 并带有`高亮`显示的一段文本来自[我的Github](https://github.com/SeayXu "SeayXu")。
我是图片：
![github logo][github-img]

本文就介绍到这里，如有不足之处，可随时与我联系。

[github-img]:https://help.github.com/assets/images/site/favicon.ico
[github-url]:https://github.com/SeayXu "SeayXu"