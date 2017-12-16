---
layout: post
title:  "用jekyll在github上搭建博客"
date:   2017-12-16
categories: blog
tags: blog
author: nick
---

* content
{:toc}

用jekyll在github上搭建博客




## 环境准备

安装ruby：[ruby下载地址](https://www.ruby-lang.org/zh_cn/)  
gem代理设置：[ruby china gem仓库](https://gems.ruby-china.org/)  
安装jekyll：gem install jekyll  
安装jekyll插件：gem install jekyll-paginate  

## HyG Theme博客主题使用方法

### 1. 复制博客主题代码

可以直接 clone 、下载 或 fork 这个仓库的代码即可

### 2. 修改参数

主要修改 `_config.yml` 中的参数和自己的网站小图`favicon.ico`

`_config.yml`文件中

#### 评论信息

获取`short_name`的方法：

访问 https://disqus.com/ 或 http://duoshuo.com/ 根据提示操作即可。

```yml
# comments
# two ways to comment, only choose one, and use your own short name
# 两种评论插件，选一个就好了，使用自己的 short_name
duoshuo_shortname: #hygblog
disqus_shortname: gaohaoyang
```

运行成功后，可以在 disqus 或 多说 的后台管理页看到相关信息。

#### 统计信息

获取 百度统计id 或 Google Analytics id 的方法：

访问 http://tongji.baidu.com/ 或 https://www.google.com/analytics/ 根据提示操作即可。当然，如果不想添加统计信息，这两个参数可以不填。

```yml
# statistic analysis 统计代码
# 百度统计 id，将统计代码替换为自己的百度统计id，即
# hm.src = "//hm.baidu.com/hm.js?xxxxxxxxxxxx";
# xxxxx字符串
baidu_tongji_id: cf8506e0ef223e57ff6239944e5d46a4
google_analytics_id: UA-72449510-4 # google 分析追踪id
```

成功后，进入自己的百度统计或 Google Analytics 后台管理，即可看到网站的访问量、访客等相关信息。

### 3. 写文章

`_posts`目录下存放文章信息，文章头部注明 layout(布局)、title、date、categories、tags、author(可选)、mathjax(可选，点击[这里](https://www.mathjax.org/)查看更多关于`Mathjax`)，如下：

```
---
layout: post
title:  "对这个 jekyll 博客主题的改版和重构"
date:   2016-03-12 11:40:18 +0800
categories: jekyll
tags: jekyll 端口 markdown Foxit RubyGems HTML CSS
author: Haoyang Gao
mathjax: true
---
```

下面这两行代码为产生目录时使用
```
* content
{:toc}
```

文章中存在的4次换行为摘要分割符，换行前的内容会以摘要的形式显示在主页Home上，进入文章页不影响。

换行符的设置见配置文件`_config.yml`的 excerpt，如下：

```yml
# excerpt
excerpt_separator: "\n\n\n\n"
```

使用 markdown 语法写文章。

代码风格与 GitHub 上 README 或 issue 中的一致。使用3个\`\`\`的方式。

### 4. 本地运行

启动jekyll服务

```
jekyll serve --port 4000
```

访问：[http://127.0.0.1:4000](http://127.0.0.1:4000)

若正在使用全局代理，可能会报错502，关闭全局代理即可。

### 5. 发布到 GitHub

没什么问题，推送到自己的博客仓库即可。

## HyG Theme支持特性说明

* **使用 GitHub 风格的代码块 Markdown 写法**

    即 GFM(github flavored markdown) 的方式。
* **首页中添加摘要**

    摘要可以在每一篇 md 文件头中使用 excerpt 属性写出来。也可以在正文中，4个换行符来分割，这个设置见配置文件`_config.yml`。
* **添加归档**

    上一版中没有归档，现在专门做了一个归档页面，当文章很多时方便根据年份快速查阅。
* **添加标签**

    标签还是很有必要添加的，上一版中也没有这个功能。现在也可以根据标签查找文章了。同时标签还有一个重要的作用是，用来获取相似文章的。
* **添加分类页**

    之前的分类就是在首页中直接完成的，现在和标签和归档类似，我将分类单独制作为一页，方便查阅。
* **简化评论配置，支持 多说 和 disqus**

    在`_config.yml`中评论配置直接添加自己的`short_name`，评论就能正常使用了。
