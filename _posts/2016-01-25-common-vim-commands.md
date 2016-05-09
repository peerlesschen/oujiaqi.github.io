---
layout: post
title: Vim 常见命令总结
subtitle: 个人 Vim 学习笔记
date: '2016-01-25 19:54:01 +0800'
catalog: study
keyword: Vim，终端，Linux，编辑器
excerpt: 个人实践过程中总结的 Vim 常见命令。
tags: [Vim, 终端, 编辑器]
categories: articles study notes
header_img: 
---

- **保存 --- `:w`**

    另存为 --- `:w test.txt`

- **退出 --- `:q`**

    强制退出 --- `:q!`

- **搜索 --- `/Mary` 正则表达式形式**

    下一结果 --- `N`

    前一结果 --- `N`+`Shift`

- **跳转指定行 --- `:5`**

- **光标移动**

    `0` (零) 行首

    `Shift`+`4` ($) 行尾

    `H` 左，`J` 上，`K` 下，`L` 右

    `B` 回退一单词，`W` 前进一单词

- **删除 --- `D`**

    `X` 删单字符

    `dd` 删单行，`3dd` 删除3行

    `dw` 删除单词，`3dw` 删除3单词

- **撤销 --- `U`**

- **插入 --- `i`**

    `O` 向下新插入一行
    
    `O`+`Shift` 向上新插入一行

    `R` 替换单个字符

- **可视模式**

    `V` 以字符单位选择文本

    `V`+`Shift` 以行单位选择文本

- **文本缩进**

    `Shift`+`,` 减缩进，`Shift`+`.`增缩进

- **复制、粘贴 ---  `Y`**

    `yy` 复制单行
    
    `yw` 复制单词

    `P` 后粘贴
    
    `Shift`+`P` 前粘贴

    `40P` 40次

    剪贴功能其实就是 `D` 之后 `P` 粘贴就好了


