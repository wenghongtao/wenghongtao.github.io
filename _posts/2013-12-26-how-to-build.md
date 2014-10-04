---
layout: post
title: 如何利用GitHub Pages和Jekyll Bootstrap搭建博客
category: JekyllBootstrap
tags: [jekyll, bootstrap]
---
{% include JB/setup %}

## 前言

GitHub相信大家都不会陌生，号称程序员的Facebook，许多知名的开源项目，例如Bootstrap、Jekyll，都托管在这个网站上面。

今天，我会给大家介绍自己如何利用GitHub Pages和Jekyll Bootstrap搭建博客。基于以上主题，我认为你已经有使用GitHub经验，所以不会详细介绍Git的安装和GitHub的托管过程。


## GitHub Pages和Jekyll Bootstrap简介

GitHub是一个非常流行的代码托管网站，而GitHub Pages则是GitHub为方便托管在上面的项目的一个项目简介站点，个人、组织也可以通过GitHub Pages建立博客。

GitHub Pages支持[Jekyll](http://jekyllrb.com/)（一个静态站点生成器，根据网页源码生成静态HTML等文件）来建立博客，只要在本地搭建一个符合Jekyll规范的静态网站，上传到GitHub后会帮你托管整个网站。

通过GitHub Pages搭建网站的优点是：

* 免费，有300MB空间。
* 不需要搭建服务器，同时拥有很高的定制能力。
* 通过Git进行版本管理。
* 需要的话可以绑定域名。

当然也有缺点：

* 使用Jekyll，只能发布静态页面，不适合大一点的网站。
* 有一点技术门槛，需要对网页开发、Git、Jekyll有一定了解。
* 由于是静态页面发布，没有像评论等动态的功能，不过可以通过外部服务来解决。


## 搭建Jekyll环境

学习一门语言，最烦人的无疑是搭建环境了，而利用Jekyll Bootstrap搭建博客也同理，因为之前没接触过Ruby，而Jekyll恰恰是用Ruby写的一个内容生成器，因此也要搭建本地jekyll环境。我搭建Jekyll环境的过程也十分蛋疼，不过好在前人已经帮忙填了很多坑。具体的过程不在这里多说，有机会的话可能另开一篇博文讲讲具体的过程，这里可以参考这篇文章————[windows下本地jekyll博客搭建手记](http://blog.jsfor.com/skill/2013/09/07/jekyll-local-structures-notes/)。

概要过程(Windows平台，其他平台类似)就是：

* 到[Rubyinstaller](http://rubyinstaller.org/)下载相应的Rubyinstaller和Development Kit（如64位的Windows需要Ruby 2.0.0-p353 (x64)和DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe），然后解压DevKit到C:\DevKit目录。
* 打开CMD，逐一输入以下命令：
<pre><code>gem update --system

cd C:\DevKit

ruby dk.rb init

ruby dk.rb install

gem install jekyll

gem install rdiscount
</code></pre>
	
成功之后可以通过`jekyll -v`来查看是否安装成功，通过`jekyll serve`来启动服务器。不过有几点需要注意：

* 由于Jekyll项目默认是ANSI编码，所以需要在_config.yml里面配置encoding: utf-8，另外，如果有中文的文件注意编码必须是UTF-8格式。
* 由于网络的原因可能会提示出错，只要把ruby下载的cache目录所有的文件都删除，类似c:/ruby/lib/ruby/gems/1.8/cache这样的目录（根据你自己的版本推算），再重新安装就好了。
* 如果是老的版本还需要添加环境变量，请自行谷歌之。
* 还有一点，本地请求地址并不是提示的http://0.0.0.0:4000，而是http://127.0.0.1:4000。


## 建立GitHub Pages

[GitHub Pages](http://pages.github.com/)页面上有介绍如何建立一个GitHub Pages项目。

![GitHub Pages](/assets/images/githubpages.jpg)

主要的步骤（参考官方介绍）是：

* 在GitHub上建立一个新项目，并且以*username*.github.io命名，其中*username*为你的GitHub用户名（或者组织的名字）。
![GitHub Pages](/assets/images/newrepo.png)

* 把项目clone到本地目录。
<pre><code>git clone https://github.com/<i>username</i>/<i>username</i>.github.io
git checkout master
</code></pre>

* 在项目目录下面新建index.html。
<pre><code>cd <i>username</i>.github.io
echo "Hello World" > index.html
</code></pre>

* Push到GitHub远程仓库。
<pre><code>git add --all
git commit -m "Initial commit"
git push
</code></pre>

好了，现在你可以访问你的GitHub Pages了，域名就是*username*.github.io，*username*你懂的。


## 使用Jekyll Boostrap

现在可以访问你的页面了，可是只有一个页面，而且空空如也，咋办？

不用担心，GitHub已经替你想好了。Jekyll是GitHub支持和推荐的一个静态模板解析引擎，而且你可以选取[Jekyll Bootstrap](http://jekyllbootstrap.com/)上面的不同主题的模板，大大简化了我们的工作。

使用默认的Jekyll Bootstrap主题（twitter bootstrap）之前，注意由于刚开始建立GitHub Pages时候我们手动新建了index.html，记得删掉，这样访问的时候会转到Jekyll Bootstrap的默认页面，之后的步骤是：

* 将GitHub上的Jekyll Bootstrap的主题clone到项目目录下。
<pre><code>git clone https://github.com/plusjade/jekyll-bootstrap.git <i>username</i>.github.io
cd <i>username</i>.github.io
git remote set-url origin git@github.com:<i>username</i>/<i>username</i>.github.io.git
git push origin master
</code></pre>

* 启动本地服务：
<pre><code>cd <i>username</i>.github.io
jekyll serve
</code></pre>

* 本地查看博客效果：访问http://localhost:4000/。

* 也可以查看GitHub Pages上的站点：*username*.github.io。

## 改造主题

好了，下一步是改造你的主题了。由于目前我的博客还在改造之中，所以我会把我改造的经验在下一篇博文中分享给大家。
