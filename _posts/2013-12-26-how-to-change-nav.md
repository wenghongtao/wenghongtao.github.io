---
layout: post
title: 如何修改JekyllBoostrap导航栏
category: JekyllBootstrap
tags: [jekyll, bootstrap]
---
{% include JB/setup %}

### 前言

今天开始动手改造Jekyll Bootstrap的twitter主题，Let's Go!

动手之前最好先了解下[Markdown](http://wowubuntu.com/markdown/)和[YAML](http://www.yaml.org/)，另外我相信当你读这篇文章的时候已经了解过[Jekyll](http://jekyllrb.com/)和[Jekyll BootStrap](http://jekyllbootstrap.com/)了。

### 定位

刚开始没有认真看配置文件（\_config.yml），就在\_layouts和\_includes目录里瞎找，后来又百度谷歌了一翻，浪费了很多时间。

后来才发现在_config.yml文件中的属性“JB”下面可以配置，像“archive_path”，“categories_path”，“tags_path”，要注意的是，这个是配置单个导航按钮页面的信息，如“archive_path”配置的是归档的页面。配置文件里面可以在YAML头信息里面设置对应页面的信息和样式，例如标题、layout文件等，记得添上“group: navigation”不然导航栏不会显示这个导航按钮。还要注意一点，就是YAML文件头格式是“property: value”，属性后面紧跟冒号，冒号后面要有空格，不然也会出问题。

### 按需修改
根据文件的格式，你可以把原本的Archive、Categories等英文导航按钮改成中文的，也可以根据自己的需要增加或修改导航按钮。

好了，现在你也可以去试试给你的博客改下导航栏。