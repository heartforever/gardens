---
layout: page
title: 初遇jekyll
categories: [jekyll, gitHub-page]
---

# {{ page.title }}

## 初步搭建github-page + jekyll的体验

### 1. 关于github-page

本人直接用的github申请的账号 + mac客户端，省去了本地用git创建仓库上传到gitbub并添加认证的过程。

github-page的创建过程见官网[github page](https://pages.github.com/ "GitHub Page")

### 2. 关于jekyll

jekyll的基本语法参考官网，[Jekyll](https://jekyllrb.com/docs/ "Jekyll")，唯一不好的是没有注释。
因为我的mac上装了各种乱七八糟的东西，jekyll直接就装上了，看官网需要已安装：

*   ruby
*   rubygems
*   linux/unix/mac osX
*   nodejs
*   python2.7

#### 个人认为几个比较重要的章节：

*   [目录结构](https://jekyllrb.com/docs/structure/ "structure")
*   [配置](https://jekyllrb.com/docs/configuration/ "configuration")
*   [最简单的页面](https://jekyllrb.com/docs/posts/ "posts")
*   [系统变量](https://jekyllrb.com/docs/variables/ "variables")
*   [使用自己的数据](https://jekyllrb.com/docs/collections/ "collections")
*   [自定义数据](https://jekyllrb.com/docs/datafiles/ "datafiles")
*   [filter和tag](https://jekyllrb.com/docs/templates/ "templates")
*   [永久链接](https://jekyllrb.com/docs/permalinks/ "permalinks")
*   [分页](https://jekyllrb.com/docs/pagination/ "pagination")
*   [插件](https://jekyllrb.com/docs/plugins/ "plugins")

#### 扩展知识：

*   sass
*   yaml
*   liquid

### 3.遇到的问题

#### 加载资源文件的方式

css文件至少可以从一下几种方式载入：

*   系统目录/css，只支持sass/scss格式
*   /include 未使用
*   /assets，系统资源路径，我把css，js等资源都放在了这里。但是图片用的系统文件夹 /img

#### 统计包含文章最多的分类

<p>这个没找到完全中意的资料，不是太复杂就是不符合需求。最终解决方案如下：</p>
<p>\{\% for category in site.categories | sort: last.size | first limit:1 \%\} </p>

*   site.categories获取所有分类
*   sort: last.size根据分类文章数量排序
*   limit:1 只取第一个

但是此写法liquid语法检查会有异常
