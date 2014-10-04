---
layout: post
title: 关于Jekyll解析中文的问题
category: JekyllBootstrap
tags: [jekyll, bootstrap]
excerpt: 使用Jekyll的过程中发现其对中文支持不够友好，这边博文记录了我是如何解决Jekyll对中文的解析问题。
---
{% include JB/setup %}

## 1. 解析中文的页面：
刚开始没有修改配置文件，直接运行服务器`jekyll serve`，提示出错： 
 
>Generating... Error reading file I:/Program Files (x86)/...: invalid byte sequence in GBK  
>    
>error: invalid byte sequence in GBK. Use --trace to view backtrace

原来Jekyll对中文支持不够友好，需要在_config.yml增加一行配置：`encoding: utf-8`