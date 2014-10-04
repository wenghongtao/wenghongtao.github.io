---
layout: post
title: 设置Disqus模块显示中文的界面
category: JekyllBootstrap
tags: [disqus]
---
{% include JB/setup %}


目前我的博客用的是国外的Disqus评论服务，但是我发现Disqus默认使用英文的界面，于是打算到官网修改成中文的界面。遗憾的是，目前Disqus还不支持中文，中文本地化工作还在紧张地进行中。-_-! 

谷歌了一下，发现Disqus原本支持中文的，因为后来升级了而翻译工作没跟上，导致现在不支持中文了。另外，我还找到了一篇文章介绍使用繁体中文的办法，虽然有点投机取巧，但是利用这个原理还是能解决使用简体中文的问题。现在我把这个方法介绍给大家，详细的步骤如下（有HTML基础的同学可以跳过这部分，直接看原理的部分）：

### 1. 登录你的Disqus账号，进入Settings界面。

![settings](/assets/images/disqusset.jpg)

### 2. 鼠标移到Language右侧的下拉列表处，点击鼠标右键，选择审查元素。

![选择审查](/assets/images/disqussel.jpg)

### 3. 此时会弹出一个窗口，找到`<select name="forum_language">`一栏，点击鼠标右键，选择`Edit as HTML`，出现一个可编辑的小框。

![审查界面](/assets/images/disqusins.jpg)

### 4. 在小框第一行`<select name="forum_language">`下面粘贴下面的代码，如图所示：  
	<option value="zh">
		Chinese
	</option>

![添加后界面](/assets/images/disqusadd.jpg)
	
### 5.把正在编辑的窗口最小化或者直接回到原来的网页，重新查看可选择的Language，可以看到多了Chinese！好了，现在可以选中并提交，大功告成。

![添加成功](/assets/images/disqusres.jpg)

## 原理 

* Disqus的评论系统升级后并没有禁掉原来使用其他语言的API，只是从下拉列表移除了部分选项，因此，通过向系统提交原本支持的语言的选项，仍然能使用原来的本地化界面。
* 如果想要Disqus支持中文界面，需要在网站的Settings页面，找到表单settings-form的关于Languages代码，也就是`<select name="forum_language">`。
* 在select之中增加一项值为`zh`的option，之后在下拉列表选中并提交到服务器，代码如下：

		<option value="zh">
			Chinese
		</option>


##### PS：现在这个方法只是权宜之计，可能会出现不稳定或者仍翻译为英文的地方，不过从官网看到目前中文翻译的工作已经进行到64%了，相信Disqus很快就支持中文的界面。另外本文参考了另一篇文章——[Disqus 繁體中文設定方法教學](http://yesdesigning.com/thread-360-1-1.html)，有兴趣的可以看看。












