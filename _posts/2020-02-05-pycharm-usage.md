---
layout: post
title: PyCharm 使用技巧
date: 2020-02-05
categories: Programming
tags: Python
status: publish
type: post
published: true
author: Quebradawill
---

### 1. 代码排版，自动PEP8

1）安装 Python 代码自动排版为 PEP8 风格的工具，`pip install autopep8`<br>2）autopep8 的配置：打开 File $\to$ Setting... $\to$ External Tools，点击“+”，Name：autopep8，Description：autopep8，Program：autopep8，Arguments：`--in-place --aggressive $FilePath$`，Working directory：`$ProjectFileDir$`，Output filters：`$FILE_PATH$\:$LINE$\:$COLUMN$\:.*`

### 2. 误删文件，一秒找回

在你的项目目录里，点击右键，有个 `Local History` 的选项，再点击子选项 `Show History`，你可以看到这里有个记录板。如果你想恢复删除的文件，就在删除的记录项点击右键，选择 `Revert` 即可恢复。

### 3. 代码模板，效率编码

File $\to$ File and Code Templates，PyCharm 提供的这个代码模板，可以说是相当实用的一个功能了。它可以在你新建一个文件时，按照你预设的模板给你生成一段内容，比如解释器路径，编码方法，作者详细信息等。

在编写代码过程中也可以敲 `Ctrl+J`，弹出 Live Templates。

### 4. 关闭烦人的灯泡提示

先来说下这个灯泡提示是什么，有什么用？

当我们在代码里面有语法错误，或者代码编写不符合 pep8 代码规范时，鼠标选择有问题的代码，就会自动弹出小灯泡，这个灯泡是有颜色之分的，如果是红灯泡，一般都是语法问题，如果不处理会影响代码运行。而如果是黄灯泡，就只是一个提示，提示你代码不规范等，并不会影响程序的运行。

虽然这个灯泡，是出于善意之举，但我认为它确实有点多余（可能是我个人没有使用它的习惯），要是语法错误会有红色波浪线提示。你可能会说灯泡不仅起到提示的作用，它还可以自动纠正代码，我个人感觉并没有人工校正来得效率，来得精准。

基于有时还会像知乎上这个朋友说的这样，会挡住我们的代码，会经常误点，这确实也是一个烦恼。

Pycharm （2018 版本）里是有开关按钮的，将选项（File $\to$ Settings... $\to$ Editor $\to$ General $\to$ Appearance $\to$ Show intention bulb）取消勾选，就可以关闭这个功能。

### 5. 关闭碍眼的波浪线

Pycharm 本身会实时地对变量名进行检查，如果变量名不是一个已存在的英文单词，就会出现一条波浪线，当一个变量里有多个单词时，Python 推荐的写法是用下划线来分隔（其他语言可能会习惯使用**驼峰式命名法**，但 Python 是使用下划线），那么如何关闭这个非语法级别的波浪线呢？很简单，它的开关就在你的右下角那个像 人头像 一样的按钮。

### 6. 运行代码的几种方式

**1. 直接运行（Shift+F10）**

**2. 调试运行（Shift+F9）**

**3. 运行选中代码：**选中代码，右键菜单里选择“Execute Selection in Python Console (Alt+Shift+E)”。

**4. 分段执行代码：**1）在想要分段运行的段的前一行（空白行）输入 `#%%`；2）选择 Scientific Mode；3）运行程序。

PyCharm 在 2017.3 版本之后加入了 Scientific Mode，在科学计算时，可以方便的追踪变量变化等。有时打开了 scientific mode 时，但文件中引入了 numpy 等科学计算包时并没有被自动识别，以 scientific mode 运行。需要在 run 方法中手动设置一下。

具体步骤：<br>1）File $\to$ Settings... $\to$ Tools $\to$ Python Scientific，勾选 Show plots in tool window；<br>2）View 菜单中勾选 Scientific Mode；<br>3）Run $\to$ Edit Configurations… 中勾选 Run with Python Console

### 7. PyCharm 中设置代码提示不区分大小写

对于 2018.2 版以后的版本，按如下方法设置：File $\to$ Settings... $\to$ Editor $\to$ General $\to$ Code Completion，取消 “Match case”的复选。

### 8. 选定内容敲引号、括号括住

File $\to$ Settings... $\to$ Editor $\to$ General $\to$ Smart Keys，复选 Surround selection on typing quote or brace

### 9. 设置比较大的换行

File $\to$ Settings... $\to$ Editor $\to$ Code Style，设置 Hard warp at 中比较大的数值。

### 10. 鼠标滑轮改变字号大小

File $\to$ Settings... $\to$ Editor $\to$ General，复选 Change font size (Zoom) with Ctrl+Mouse Wheel

### 11. 保存当前窗口布局

Windows $\to$ Store Current Layout as Default

### 12. 新版 PyCharm 中 Matplotlib 图像不再弹出独立的显示窗口

PyCharm 从 2017.3 版之后，将 `matplotlib` 的绘图的结果默认显示在 `SciView` 窗口中，而不是弹出独立的窗口。如果要弹出独立窗口，则需取消勾选：File $$\to$$ Settings $$\to$$ Tools $$\to$$ Python Scientific $$\to$$ Show plots in tool window。

### 13. 让 PyCharm 运行程序时只打开一个 Python Console

1) 改变单个文件默认运行方式：取消 Run $$\to$$ Edit Configuration $$\to$$ Run with Python Console 复选；<br>2) 修改整体运行方式：取消 Run $$\to$$ Edit Configuration $$\to$$ Templates $$\to$$ Python $$\to$$ Run with Python Console 复选。

### 14. 新版 PyCharm 中 Matplotlib 图像不再弹出独立的显示窗口

PyCharm 从 2017.3 版之后，将 `matplotlib` 的绘图的结果默认显示在 `SciView` 窗口中，而不是弹出独立的窗口。如果不喜欢这种设置，可以通过如下方式修改，取消复选，File $\to$ Settings $\to$ Tools $\to$ Python Scientific $\to$ Show plots in toolwindow，将弹出独立窗口。

有时需做如下更改：

```python
import matplotlib
matplotlib.use('TkAgg')
print(matplotlib.get_backend())
```

常见的 backend 有 TkAgg、Qt4Agg、Qt5Agg 等等。

### 15. 关于 Pycharm 无法 debug 问题的总结

**问题描述：**在 PyCharm 中写 Python 时可以运行程序却突然不能 debug。出现 debug 提示——pydev debugger: process xxxx is connecting，但是之后却一直处于等待连接状态而报错。

**与该错误相关的网上的解决方案：**

解决方案一：PyCharm 的网络被禁，需要解禁网络。

解决方案二：去掉 ".idea"文件重启项目。

尝试了所有的方案后还是不能解决我的问题，突然发现众多报错信息中有一个 attributeerror: 'queue' object has no attribute 'put'。

难道和我自己写的 queue.py 文件中的 queue 类有关？

**更改了 queue.py 的文件名后问题解决！**

原因大概是自己创建的 queue.py 文件代替了 Python 3 中自带的同名文件被调试程序调用而出错。

### 16. PyCharm 新建文件具有相同文件头

File $\to$ Settings $\to$ File and Code Templates，选中“Python Script”，输入如下：

```python
# encoding: utf-8
"""
@author: Quebradawill
@license: (C) Copyright 2010-2020.
@contact: dwqiu@foxmail.com
@software: PyCharm
@filename: ${NAME}.py
@datetime: ${DATE} ${TIME}
@desc:
"""


```

### 17.

**参考：**

1、[PyCharm 使用技巧](https://www.cnblogs.com/xxtalhr/p/11083279.html)

