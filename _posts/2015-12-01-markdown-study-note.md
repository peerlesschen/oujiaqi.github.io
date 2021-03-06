---
layout: post
title: Markdown 学习笔记
subtitle: 注意细节 你能走更远
date: '2015-12-01 23:22:24 +0800'
catalog: study
keyword: Markdown 学习笔记，Markdown语法。
excerpt: Markdown 是一种轻量级的「标记语言」，它的优点很多。Markdown 的语法十分简单，常用的标记符号也不超过十个，十分轻量易学。学会 Markdown 让你更专注写东西。这是我学习 Markdown的笔记。
tags: [Markdown, 工具]
categories: articles study notes
header_img: 
---


## 概述

### 综述

易读易写

### 兼容HTML

HTML的书写语言，HTML做发布。Markdown会自动生成相应的HTML标签。

部分未涵盖的标签，可以直接加入，Markdown会自动识别不会重复添加，诸如`<div>`、`<table>`、`<pre>`、`<p>`等标签。

Markdown语句如下：

```
这是一个普通段落。

<table>
	<tr>
		<td>Foo</td>
    </tr>
</table>

这是另一个普通段落。
```

效果如下：

------

这是一个普通段落。

<table>
	<tr>
		<td>Foo</td>
    </tr>
</table>

这是另一个普通段落。

------

### 特殊字符自动转换

`<`和`&`等字符在HTML中，转码比较麻烦，Markdown会帮你自动转换。举几个例子: `&copy; AT&T` ->  &copy; AT&T，`4<5` -> 4<5

注意：code范围内，不论行内还是区块，<和&两个符号都 ***一定*** 会转换成HTML实体

## 区块元素

### 段落和换行

段落之间要有一个以上的空行（空行的定义是显示上看起来像是空的，便会视为空行，比如某一行只包含空格和制表符，则该行会视为空行）

Markdown默认段落之间换行，既`<br />`

### 标题

Markdown语句如下：

```
This is an H1(三个以上`=`)
========

This is an H2(`-`)
--------

# H1

## H2

### H3

#### H4

##### h5

###### h6
```

***行尾加`#`纯属为了美观，可加可不加，加的话就对称***

效果如下：

------

This is an H1(三个以上`=`)
========

This is an H2(`-`)
--------

# H1

## H2

### H3

#### H4

##### h5

###### h6

------


### 区块引用 *Blockquotes*

Markdown语句如下：

```
> ## 这是一个标题
> 
> > This is nested blockquote
>
> 1. 这是第一行
> 2. 只是第二行
```

效果如下：

------

> ## 这是一个标题
> 
> > This is nested blockquote
>
> 1. 这是第一行
> 2. 只是第二行

-----

### 列表

Markdown 语句如下：

```
* Red
* Green
* Blue
+ A
+ B
+ C
- d
- f

1. ou
2. jia
3. qi
```

效果如下：

------

* Red
* Green
* Blue
+ A
+ B
+ C
- d
- f

1. ou
2. jia
3. qi

------

Markdown 语句如下：

```
1. wo
1. jiao
1. oujiaqi
```

效果如下：

------

1. wo
1. jiao
1. oujiaqi

------



如果列表项目间用空行分开，在输出HTML时会用`p`标签包起来

```
* bird
* magic
```

对应HTML为：

```
<ul>
<li>Bird</li>
<li>Magic</li>
</ul>
```

但是

```
* Bird

* Magic
```

对应HTML为：

```
<ul>
<li><p>Bird</p></li>
<li><p>Magic</p></li>
</ul>
```

避免出现列表。换句话说，也就是在行首出现数字-句点-空白，要避免这样的状况，你可以在句点前面加上反斜杠。

```
1986\.what a great season.
```

### 代码区块
四个空格或一个制表符，或者使用 \`\`\`包裹起来的部分区域

Markdown 语句如下：

```
这是一个普通段落

    这是一个代码区域（前面有四个空格或一个制表符）
    
    ```
    这也是一个代码区域
    ```
```

对应的效果如下：

------

这是一个普通段落

    这是一个代码区域（前面有四个空格或一个制表符）
    
    
```
这也是一个代码区域
```

------

### 分隔线
三个以上的星号、减号、底线，行内不能有其他东西。中间可以插入空格

Markdown语句如下：

```
* * *
***
*****
- - -
---------------------------------------
```

都是对应横线：

------

## 区段元素

### 链接

#### 行内式

Markdown 语句如下：

```
This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.

连接到同样主机资源，相对路径：
See my [About](/about/) page for details.
```

对应效果如下：

------

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.

连接到同样主机资源，相对路径：
See my [About](/about/) page for details.

------

#### 参考式

Markdown 语句如下：

```
This is [an example][id] reference-style link. 

或者中间可以空格

This is [an example] [id] reference-style link.

接着在文件任意处，将这个标记的连接内容定义出来

[id]: http://example.com/ "title"

如下定义方式，中间最多三个空格
[foo]: http://example.com/  "Optional Title Here"

[foo]: http://example.com/  'Optional Title Here'

[foo]: http://example.com/  (Optional Title Here)
```

显示效果如下：

------

This is [an example][id] reference-style link. 

或者中间可以空格

This is [an example] [id] reference-style link.

[id]: http://example.com/ "title"

------

***注意，标签不区分大小写***

### 强调

Markdown语句如下：

```
*斜体* _斜体_
**加粗** __加粗__
***斜加粗*** ___斜加粗___

特殊的用反斜杠
例如
\* ok \*
```

显示效果如下：

------

*斜体* _斜体_
**加粗** __加粗__
***斜加粗*** ___斜加粗___

特殊的用反斜杠
例如
\* ok \*

------

### 代码

标记一小段代码，用\`\`包起来

Markdown 语句如下：

```
Use the `printf()` function.
```

显示效果如下：

Use the `printf()` function.

### 图片

#### 行内式

Markdown 语句如下：

```
![](http://pic.58pic.com/58pic/12/57/77/48258PICBCH.jpg "title")
```

显示效果如下：

------

![](http://pic.58pic.com/58pic/12/57/77/48258PICBCH.jpg "title")

------

#### 参考式

Markdown 语句如下：

```
![Alt text][id]

[id]: http://pic.58pic.com/58pic/12/57/77/48258PICBCH.jpg "V"
```

显示效果如下：

------

![Alt text][id]

[id]: http://pic.58pic.com/58pic/12/57/77/48258PICBCH.jpg "V"

------

## 其他

### 反斜杠

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号

Markdown 语句如下：


```
\\   反斜线
\`   反引号
\*   星号
\_   底线
\{\}  花括号
\[\]  方括号
\(\)  括弧
\#   井字号
\+   加号
\-   减号
\.   英文句点
\!   惊叹号
```

对应效果为：

------

\\   反斜线 
\`   反引号 
\*   星号 
\_   底线 
\{\}  花括号 
\[\]  方括号 
\(\)  括弧 
\#   井字号 
\+   加号 
\-   减号 
\.   英文句点 
\!   惊叹号 

------

### 自动链接

Markdown 语句如下：

```
<http://example.com/>
```

显示效果如下：

------

<http://example.com/>

------

## 补充

Markdown 语句如下：

```
插入表格

|   中间   |   左边    |   右边对齐    |
|:---------:|:------|------:|
|Animal another adf |Descripiton just for test |Price right|
|Gnat| pergram| 13.65|
|Gnat| pergram| 13.65|
|Gnat| pergram| 13.65|
|Gnat| pergram| 13.65|

书写一个质能守恒公式

$$E=mc^2$$

高亮一段代码

    ```python
    @requires_authorization
    class SomeClass:
        pass
    
    if __ name__ == "__main__":
        # A comment
        print "hello world"
    ```
```

对应效果如下：

------

插入表格

|   中间   |   左边    |   右边对齐    |
|:---------:|:------|------:|
|Animal another adf |Descripiton just for test |Price right|
|Gnat| pergram| 13.65|
|Gnat| pergram| 13.65|
|Gnat| pergram| 13.65|
|Gnat| pergram| 13.65|

书写一个质能守恒公式

$$E=mc^2$$

高亮一段代码

```python
@requires_authorization
class SomeClass:
    pass
if __ name__ == "__main__":
    # A comment
    print "hello world"
```

------

## 几个关于Markdown的链接

- [认识与入门 Markdown](http://sspai.com/25137)
- [Markdown——入门指南 - 简书](http://www.jianshu.com/p/1e402922ee32/)
- [创始人 John Gruber 的 Markdown 语法说明](http://daringfireball.net/projects/markdown/syntax)
- [Markdown 中文版语法说明](http://wowubuntu.com/markdown)
- [Windows/Mac/Linux 全平台客户端](https://www.zybuluo.com/cmd/)
- [Cmd Markdown 在线编辑器](https://www.zybuluo.com/mdeditor)
- [好用的Markdown编辑器一览](http://www.williamlong.info/archives/4319.html)



















