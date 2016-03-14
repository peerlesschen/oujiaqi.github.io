---
layout: post
title: Liquid 模板语言学习笔记
date: '2016-12-12 22:57:01 +0800'
categories: notes skills
excerpt: Liquid 模板语言
---

[Liquid](https://docs.shopify.com/themes/liquid)是一门用Ruby编写的开源的模板语言
## Basics
### Handles
用于获取Liquid对象的属性。默认情况下，handle是对象的标题经过小写字母转换，(-)替代特殊符号或者空格后。例如

```html
<!-- the content of the About Us page -->
{{ pages.about-us. content }}
```

#### Handles 创建方式
- 大写转小写，同名自动表序号。"Shirt"变“shirt"，多个变“shirt-1”，“shirt-2”等
- 空格或特殊字符变`-`

#### 获取属性方法

```html
{{ pages.about-us.title }}
{{ pages["about-us"].title }}

{% for product in collections[settings.home_featured_collection].products %}
    {{ product.title }}
{% endfor %}
```

### Operators
#### Basic operators
`==``!=``>``<``>=``<=``or``and`
#### The contains Operator

```html
{% if product.title contains "pack" %}
  This product's title contains the word Pack.
{% endif %}
```

### Data types

1. String: `assign my_string = "Hello World!"`
2. Number
3. Boolean: true and false
4. Nil: 相当于None，空，也为false、
5. Array: 用for语句获取或者`[ ]`获取
6. EmptyDrop: An EmptyDrop object is returned if you try to access a deleted object (such as a page or post) by its handle. EmptyDrop objects only have one attribute, `empty?`, which is always true. 可以用来检测是否对象存在

### Truthy and falsy
除了`nil``false`，都是 true，空的字符串也是true，空的字符串可以用 `blank`检测，`stringA == blank`，EmptyDrop也为true

## Tags
### Control flow tags

`if` `else` `elsif`

```html
 <!-- If customer.name = 'anonymous' -->
  {% if customer.name == 'kevin' %}
    Hey Kevin!
  {% elsif customer.name == 'anonymous' %}
    Hey Anonymous!
  {% else %}
    Hi Stranger!
  {% endif %}
```

`case` `when`

```html
{% assign handle = 'cake' %}
{% case handle %}
  {% when 'cake' %}
     This is a cake
  {% when 'cookie' %}
     This is a cookie
  {% else %}
     This is not a cake nor a cookie
{% endcase %}
```

`unless` 除非，除开

### Iteration tags

`for`

```html
{% for product in collection.products %}
    {{ product.title }}
{% endfor %}
```

`break` 结束

```html
{% for i in (1..5) %}
    {% if i == 4 %}
      {% break %}
    {% else %}
      {{ i }}
    {% endif %}
{% endfor %}
```

`continue` 继续

```html
{% for i in (1..5) %}
    {% if i == 4 %}
      {% continue %}
    {% else %}
      {{ i }}
    {% endif %}
{% endfor %}
```

`limit` for 的限制

```html
<!-- if array = [1,2,3,4,5,6] -->
  {% for item in array limit:2 %}
    {{ item }}
  {% endfor %}
<!-- output 1 2 -->
```

`offset`

```html
<!-- if array = [1,2,3,4,5,6] -->
  {% for item in array offset:2 %}
    {{ item }}
  {% endfor %}

<!-- output 3 4 5 6 -->
```

`range` 数字或变量都可以

```html
{% assign num = 4 %}
{% for i in (1..num) %}
  {{ i }}
{% endfor %}

{% for i in (3..5) %}
  {{ i }}
{% endfor %}
```

`reversed` 倒序

```html
<!-- if array = [1,2,3,4,5,6] -->
{% for item in array reversed %}
    {{ item }}
{% endfor %}
```

`cycle` 循环取值，必须在for循环中

```html
{% cycle 'one', 'two', 'three' %}
{% cycle 'one', 'two', 'three' %}
{% cycle 'one', 'two', 'three' %}
{% cycle 'one', 'two', 'three' %}

<!-- output one two three one -->
```

`cycle group` 防止上下cycle混用，以分开。

```html
<ul>
{% for product in collections.collection-1.products %}
  <li{% cycle 'group1': ' style="clear:both;"', '', '', ' class="last"' %}>
    <a href="{{ product.url | within: collection }}">
      <img src="{{ product.featured_image.src | product_img_url: "medium" }}" alt="{{ product.featured_image.alt }}" />
    </a>
  </li>
{% endfor %}
</ul>
<ul>
{% for product in collections.collection-2.products %}
  <li{% cycle 'group2': ' style="clear:both;"', '', '', ' class="last"' %}>
    <a href="{{ product.url | within: collection }}">
      <img src="{{ product.featured_image.src | product_img_url: "medium" }}" alt="{{ product.featured_image.alt }}" />
    </a>
  </li>
{% endfor %}
</ul>
```

```tablerow```  制作表格`table`,必须在table标签内

```html
<table>
{% tablerow product in collection.products %}
  {{ product.title }}
{% endtablerow %}
</table>

<!-- 一行多列 -->
```

`cols` 定义列数 `limit` 限制个数  `offset` 间隔取数  `range` 范围取数     使用同 for 循环

```html
{% tablerow product in collection.products cols:2 offset:3 %}
  {{ product.title }}
{% endtablerow %}
```

### Theme tags

#### comment

解释作用，不读取

```html
My name is {% comment %}super{% endcomment %} Shopify.
```

#### include

用于插入某片段

使用`with`赋值

有一片段 colo.liquid

```html
color: '{{ color }}'
shape: '{{ shape }}'
```

theme.liquid

```html
{% assign shape = 'circle' %}
{% include 'color' %}
{% include 'color' with 'red' %}
{% include 'color' with 'blue' %}
{% assign shape = 'square' %}
{% include 'color' with 'red' %}
```

output

```html
color: shape: 'circle'
color: 'red' shape: 'circle'
color: 'blue' shape: 'circle'
color: 'red' shape: 'square'
```

#### form

#### layout

```html
<!-- loads the templates/alternate.liquid template -->
{% layout 'alternate' %}
```

```html
{% layout none %}
```

#### paginate

标页码

```html
{% paginate collection.products by 5 %}
  {% for product in collection.products %}
    <!--show product details here -->
  {% endfor %}
{% endpaginate %}
```

#### raw 

原生

```html
{% raw %}{{ 5 | plus: 6 }}{% endraw %} is equal to 11.

<!-- output {{ 5 | plus: 6 }} is equal to 11. -->
```

### Variable tags

#### assign

定义新变量

```html
{% assign foo = "bar" %}
{{ foo }}
```

#### capture

捕获并赋值给变量

```html
{% capture my_variable %}I am being captured.{% endcapture %}
{{ my_variable }}
```

#### increment

自增长，默认初始从0，不收assign影响。

```html
{% increment variable %}
{% increment variable %}
{% increment variable %}

<!-- output 0 1 2 -->
```

#### decrement

同 increment 初始为-1

## Object




未完待续。。