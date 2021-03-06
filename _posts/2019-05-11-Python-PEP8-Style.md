---
layout: post
title: PEP 8 风格指南
date: 2019-05-11
categories: Programming
tags: Python
status: publish
type: post
published: true
author: Quebradawill
---

PEP 是 Python Enhancement Proposal 的缩写，通常翻译为“Python 增强提案”。

**空格的使用**

- 使用**空格**来表示缩进而不要用制表符（Tab）。<br>
- 和语法相关的每一层缩进都用 **4 个空格**来表示。<br>
- 每行的字符数不要超过 **79 个字符**，如果表达式因太长而占据了多行，除了首行之外的其余各行都应该在正常的缩进宽度上再加上 4 个空格。<br>
- 函数和类的定义，代码前后都要用**两个空行**进行分隔。<br>
- 在同一个类中，各个方法之间应该用**一个空行**进行分隔。<br>
- 二元运算符的左右两侧应该保留**一个空格**，而且只要一个空格就好。

**标识符命名**

- 变量、函数和属性应该使用**小写字母**来拼写，如果有多个单词就使用**下划线**进行连接。<br>
- 类中受保护的实例属性，应该以**一个下划线**开头。<br>
- 类中私有的实例属性，应该以**两个下划线**开头。<br>
- 类和异常的命名，应该每个单词**首字母大写**。<br>
- 模块级别的常量，应该采用**全大写字母**，如果有多个单词就用下划线进行连接。<br>
- 类的实例方法，应该把第一个参数命名为 `self`，以表示对象自身。<br>
- 类的类方法，应该把第一个参数命名为 `cls` 以表示该类自身。

**表达式和语句**

- 采用内联形式的否定词，而不要把否定词放在整个表达式的前面。例如 `if a is not b` 就比 `if not a is b` 更容易让人理解。<br>
- 不要用检查长度的方式来判断字符串、列表等是否为 `None` 或者没有元素，应该用 `if not x` 这样的写法来检查它。<br>
- 就算 `if` 分支、`for` 循环、`except` 异常捕获等中只有一行代码，也不要将代码和 `if`、`for`、`except` 等写在一起，分开写才会让代码更清晰。<br>
- `import` 语句总是放在文件开头的地方。<br>
- 引入模块的时候，`from math import sqrt` 比 `import math` 更好。<br>
- 如果有多个 `import` 语句，应该将其分为三部分，从上到下分别是 <font color='blue'>Python 标准模块</font>、<font color='blue'>第三方模块</font>和<font color='blue'>自定义模块</font>，每个部分内部应该按照模块名称的字母表顺序来排列。