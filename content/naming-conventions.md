---
layout: page
title: Naming Conventions
---

# Naming conventions
(命名规范 | 命名規則)

说到命名规范，个人认为包含了目录，文件以及变量的命名。提前先说一句，命名规则没有谁对谁错，在项目中保持一致才是关键。

混乱或错误的命名不仅让我们对代码难以理解，更糟糕的是，会误导我们的思维，导致对代码的理解完全错误。相反，良好的命名，则可以让我们的代码非常容易读懂，也能向读者正确表达事物以及逻辑的本质，从而使得代码的可维护性就大大增强，读命名好的文章是非常流畅的，会有一种享受的感觉。

* 目录
由于Windows, OSX下文件名不区分大小写(linux是区分的)，所以命名我们建议还是以全部小写为主，个人习惯连字符使用-中划线。比如: my-project-name

项目中的子目录一般按照作用，使用常用单词表示，有复数的情况，使用复数命名法，比如: scripts, styles, images和data-modules

* 文件
文件的命名我个人也是推荐使用-中划线进行连接。和目录的连接字符保持一致。但是linux系统文件推荐的文件命名一般是下划线。

* 变量
变量命名有两种方式:

    * 下划线命名法: my_variable
    * 驼峰式命名法: myVariale
当然不同语言也是有不同的规范，网上也有很多大公司的命名规范可以参考。

* JavaScript
变量推荐驼峰式命名法

* CSS
推荐使用中划线进行连接，CSS 语法本身就使用连字号作为连接（比如 font-family，text-align等）

## Python Style Guide 
[Python Style Guide](PEP-8-style-guide-for-python-code.md)