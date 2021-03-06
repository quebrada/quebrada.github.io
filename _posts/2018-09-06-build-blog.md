---
layout: post
title: GitHub + Jekyll 搭建 blog
date: 2018-09-06
categories: Programming
tags: Blog
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  views: '2'
author:
  login: Quebradawill
  email: dwqiu@foxmail.com
  display_name: Quebradawill
---

### 申请账号

- 申请一个 GitHub 账号；

- 创建一个新仓库（Repositories），注意勾选上 `Initialize this repository with a README`；

- 给自己的仓库（Repositories）命名，**注意：**名称格式为：username.github.io（username 是你 GitHub 用户名，最好不要用别的），username.github.io 将成为网站的网址；

- 进入到仓库界面，点击 settings 往下拉，找到 Github pages 设置界面，在 `source` 选项里选择 `master branch`，然后点击 save 保存。也可以在 `Theme Chooser` 里选择一个网页主题，这时候你的一个简单的网站已经搭建好了。对，你没听错，就这么简单！在 `Source` 上面出现了 `Your site is published at thhps://username.github.io/` 字样，这就是你自己网站的网址了。

### 主题美化

- 推荐从 GitHub 上下载 Jekyll 类型的模板，便于使用 Jekyll Writer 管理博文。下载后解压出网页源代码，并找到文件名为 `_config.yml` 的文件，在这个文件里面你可以修改网页的名称，要展示的内容等等；

- 然后就是把网页源代码上传到 GitHub 上刚创建的仓库里了，这里有两种方案。一种是通过 GitHub Desktop 上传，一种是通过 GitHub 网页端上传。这里介绍从 GitHub Desktop 上传；

- 打开 GitHub Desktop，点击 `file`，选择 `Clone repository`，选择 username.github.io；

- 转到 GitHub Desktop 界面，这时候它已经检测到了本地文件的变换，在左下角输入这次改动的摘要就可以上传了，点击 `Commit to master`，再点击 `Fetch origin` 完成上传。

### 在 Github.Page 渲染数学公式

在根模板文件（一般位于 `_layout` 文件夹中的 `default.html`）增加这样一句：

```html
<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
```

GitHub 里不支持有序列表，支持项目列表。

1. 在 `_includes` 文件夹下新建 `mathjax.html`，并在里面添加：

```html
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>
<script
  type="text/javascript"
  charset="utf-8"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"
>
</script>
<script
  type="text/javascript"
  charset="utf-8"
  src="https://vincenttam.github.io/javascripts/MathJaxLocal.js"
>
</script>
```

2. 在 `_layouts/post.html` 的 `Post Header` 中添加：

```html
{% include mathjax.html %}
```

3. 在想要启用 Mathjax 的文章的 [Front Matter](https://jekyllrb.com/docs/front-matter) 中添加：

```html
mathjax: true
```

参考：[个人网站的搭建（基于 GitHub 和 Jekyll 主题）](https://blog.csdn.net/qq_19799765/article/details/80869363)

在 Windows 上安装 Jekyll 的步骤：

- 安装 Ruby，获取地址 [https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)，一般选择的是 Ruby + Devkit。
- 安装 RubyGems，获取地址 [https://rubygems.org/pages/download](https://rubygems.org/pages/download)，解压缩后，在 cmd 中进入到该目录，使用命令 `ruby setup.rb` 安装；使用命令 `gem update --system` 更新到最新。
- 使用命令 `gem install jekyll` 安装 jekyll。更新软件：`gem update && gem cleanup`，如果安装错误，则可以使用如下命令：`gem sources --remove https://rubygems.org/`，`gem sources -a http://rubygems.org/`，`gem install jekyll`

参考：[Run Jekyll on Windows](http://jekyll-windows.juthilo.com)