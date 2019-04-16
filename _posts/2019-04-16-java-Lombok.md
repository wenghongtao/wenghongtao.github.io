---
layout: post
title:  "Lombok学习笔记"
categories: java
tags:  java 
author: wenghongtao
---

* content
{:toc}

Lombok学习笔记





## 前提概要
学习还是主要通过官网来：https://projectlombok.org

基本的安装就不介绍了，主要通过maven，gradle都可以，您也可以直接下载jar包，
如果需要编辑器识别不报错的话，就要下载相应的插件。官网上install里有
各个IEDs安装的方法，在此就不复述了。

### 源码学习
GitHub仓库地址：https://github.com/rzwitserloot/lombok

### 关于Java中Annotation用法

Lombok主要运用了Annotation，我们先要去了解Annotation才能，更好的理解，Lombok
是怎么自动生成get和set方法。如何自动创建构造函数

#### 1. 自定义Annotation
  1. 定义新的Annotation类型使用@interface关键字，它用于定义新的Annotation类型。定义一个新的Annotation类型与定义一个接
  口非常像，如下代码可定义一个简单的Annotation：
  
  ```
  public @interface Login {
      
  }
  ```
  
  - 给annotation添加成员变量
  
  
  ```
  public @interface Login {
      //定义两个成员变量
      String username();
      String password();
  }
  
  class LoginTest{
      /**
       * 使用注解
       */
      @Login(username="lisi", password="123456")
      public void login(){
          
      }
  }
  ``` 

 还可以定义默认值
 
 ```
  public @interface Login {
       //定义两个成员变量
       String username() default "wenghongtao";
       String password() default "123456";
   }
 ```
 
 ####  解读源码
 今天先到这里吧，我先研究一下它的源码。














