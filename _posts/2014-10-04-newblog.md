---
layout: post
title: Markdown语法笔记
category: Markdown
tags: [markdown]
---
{% include JB/setup %}

## Markdown简介

![Markdown](/assets/images/markdown.png)

Markdown是一门为了实现*易读易写*的标记语言，而且可以转化为其他的标记语言（如HTML）。这种语言吸收了很多电子邮件中的纯文本标记的特性。除了标准语法，Markdown还有很多衍生的版本，例如PHP Markdown Extra，以及GitHub上的“GitHub Flavored Markdown”（GFM）。

而本文将介绍原始的标准Markdown语法，也就是Standard Markdown(SM)。[dillinger](http://dillinger.io/)是一个在线Markdown编辑器，你可以一边阅读本文，一边练练手。

***

## 标题
一级标题可以用任意数量`=`表示，二级标题用`-`表示，也可以用1到6个`#`表示一到六级标题。

**语法示例**：

	一级标题
	===
	二级标题
	---
	# 一级标题
	## 二级标题
	### 三级标题
	#### 四级标题
	##### 五级标题
	###### 六级标题

**显示效果**：

一级标题
===
二级标题
---
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

***

## 列表

无序列表可以用`*`，`+`，`-`表示，而有序列表则用数字紧跟`.`来表示。有序列表中的数字不影响实际显示，因为HTML的有序列表`<ol>`不支持定义单项序号。列表的一项可以有多个段落，但需要缩进4个空格或1个制表符。

**语法示例**：

	* perl
	* ruby
	* python

	<!-- 注意两个列表不能相邻 --> 

	1. github
	2. jekyll
	3. bootstrap

**显示效果**：

* perl
* ruby
* python

<!-- 注意两个列表不能相邻 --> 

1. github
2. jekyll
3. bootstrap

**注意：**若两项之间用空行隔开，每项的内容会转换成被`<p>`包围起来。

	* Angry Birds
	
	* Bad Piggies

会转换成：

	<ul>
	<li><p>Angry Birds</p></li>
	<li><p>Bad Piggies</p></li>
	</ul>

***

## 链接和图片

链接和图片的语法很像，链接用`[]()`表示，而图片是`![]()`，并且可以选择加上title属性。还有另外一种形式，与论文中的参考文献很相似，具体使用请看示例。

**语法示例**：

	第一种：链接[google](http://www.google.com "search")和图片![favicon]({{ BASE_PATH }}/favicon.ico "icon")

	第二种：链接[google][1]和图片![favicon][2]

	[1]: http://www.google.com "search"
	[2]: {{ BASE_PATH }}/favicon.ico "icon"

**显示效果**：

第一种：链接[google](http://www.google.com "search")和图片![favicon]({{ BASE_PATH }}/assets/images/favicon.ico "icon")

第二种：链接[google][1]和图片![favicon][2]

[1]: http://www.google.com "search"
[2]: {{ BASE_PATH }}/assets/images/favicon.ico "icon"

***

## 强调

强调可以用`*`或者`_`表示，效果是相同的，不同数量可以分别表示斜体、粗体和粗斜体。

**语法示例**：

	表示*斜体*、**粗体**和***粗斜体***

	表示_斜体_、__粗体__和___粗斜体___

**显示效果**：

表示*斜体*、**粗体**和***粗斜体***

表示_斜体_、__粗体__和___粗斜体___

***

## 代码段

内联代码段用反引号<code>`</code>（键盘esc下面的键，不要与单引号混淆了）包围。

而块级代码段出于简洁的考虑，只需在行的开头缩进4个空格或1个制表符即可，Markdown会转换成用`<pre>`和`<code>`包围代码内容。

**语法示例**：

	这里是内联代码段`git`，

		# 这里是块级代码段
		git add .

**显示效果**：

这里是内联代码段`git`，

	# 这里是块级代码段
	git add .

**注意：**如果你需要在代码中显示反引号`` ` ``，请参考下面的写法，要显示n个反引号的话，就在外围写1 + n个反引号。

	`` ` ``

Markdown不会对代码段的代码内容进行语法转换，而像`&`和`<`这类字符会自动转换成HTML实体。例如，

	<div class="footer">
        &copy; 2014 Xaolex
    </div>

会转换成：

	<pre><code>&lt;div class="footer"&gt;
	    &amp;copy; 2014 Xaolex
	&lt;/div&gt;
	</code></pre>

***

## 水平分隔线

只需要三个或以上的`*`或者`-`就可以表示水平分隔线。

**语法示例**：
	
	***	
	---	
	* * *	
	------------

**显示效果**：

***
---
* * *
------------

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*奇葩的分割线\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

## 转义

有时候我们想要用`#`，`*`这类字符，但是他们在Markdown中有特殊的含义，所以需要转义。在Markdown中可以用反斜杠来帮助你使用这类字符。需要转义的字符如下：

	\	反斜线
	`	反引号
	*	星号
	_	底线
	{}	花括号
	[]	方括号
	()	括号
	#	井号
	+	加号
	-	减号
	.	句点
	!	惊叹号

**语法示例**：

	\#0571

	\*\*\*\*711\*\*\*\*

**显示效果**：

\#0571

\*\*\*\*711\*\*\*\*

***

## 引用

引用的用法比较简单，只需在引用内容开头加上`>`。

**语法示例**：

	> 问：“WP8应用和iOS应用的差距在哪里？”答：“iOS应用要多少有多少，WP应用要多少有多少。”
	> 
	> 中国梦.txt 美国梦.exe 日本梦.avi 朝鲜梦.bat

**显示效果**：

> 问：“WP 8 应用和 iOS 应用的差距在哪里？”答：“iOS 应用要多少有多少；WP 应用要多少有多少。
> 
> 中国梦.txt 美国梦.exe 日本梦.avi 朝鲜梦.bat

***

## 块级元素和内联元素

块级元素（区块元素）和内联元素（区段元素）其实是CSS的概念，为了帮助我们更好地在HTML中展示，有必要介绍一下。《CSS权威指南》解释：任何不是块级元素的可见元素都是内联元素。内联元素通常不会以新行开始，如同单词，相互之间可以在同一行内显示；块级元素如同段落，不可能共存于同一行。

在Markdown中，段落、标题、列表、引用、块级代码段和分割线都是块级元素，而链接、图片、强调和内联代码段都是内联元素。

**语法示例**：

	* apple
	### google
	`ms`
	*nokia*

**显示效果**：

* apple
### google
`ms`
*nokia*

***

## 自动链接

Markdown支持自动链接形式来处理网址和Email地址，这样省了我们一些写HTML的力气，也可以让写作内容一目了然，用法是使用方括号`<>`包围地址内容。

**语法示例**：

	<http://xaolex.github.io>
	
	<xaolex@gmail.com>

**显示效果**：

<http://xaolex.github.io>

<xaolex@gmail.com>

***

## 自动转换

在HTML中，`<`和`>`用于起始和结束标签，一些预留字符有特定的含义，因此这些字符需要使用[字符实体](http://www.w3school.com.cn/html/html_entities.asp)才能正确地显示。

因此在传统的HTML文件中，如果你要表示`AT&T`，则要写成`AT&amp;T`来转义，链接的`href`属性中包含`&`也同理，需要写成`&amp;`。现在使用Markdown能帮你自动处理这些元素。例如，如果你写成`AT&T`会被自动转换成`AT&amp;T`。`4<5`会自动转换成`4&lt;5`。

**语法示例**：

	AT&T
	
	&copy; Xaolex 2013
	
	1 + 1 <> 1

**显示效果**：

AT&T

&copy; Xaolex 2013

1 + 1 <> 1

***

## 内嵌HTML

Markdown目标成为一种适合网络内容的写作语言。因此，在Markdown中可以很方便地使用HTML。有一点需要注意，Markdown不会处理块级元素的Markdown语法，像`<table>`，`<div>`，`<p>`里面用强调语法`*ABC*`是无效的。

**语法示例**：

	<div>*content*</div>
	<p>**paragraph**</p>
	<span>***word***</span>
	### <a href="#">*Title*</a>

**显示效果**：

<div>*content*</div>
<p>**paragraph**</p>
<span>***word***</span>
### <a href="#">*Title*</a>

***

## 嵌套使用

引用、列表还可以嵌套使用，引用可以嵌套标题、列表等，甚至嵌套另一个引用，列表也可以嵌套另一个列表。如果想要在列表或引用中嵌入块级代码段，则需要在原有基础上缩进8个空格或2个制表符。

**语法示例**：

	> *这是引用内容*
	> > 再加个引用看看
	> 
	> * 这是引用中的列表
	> * 这是引用中的列表
	>
	
	* meat
	* vegetable
	* fruit
	  - apple
	  - pear
	  - orange

**显示效果**：

> *这是引用内容*
> > 再加个引用看看
> 
> * 这是引用中的列表
> * 这是引用中的列表
>

* meat
* vegetable
* fruit
  - apple
  - pear
  - orange

***

## 其他语法说明

* 一行中只含有空格和制表符也算空行。
* 空一行分段。
* 行尾输入两个空格加回车表示断行，即`<br>`。
* 如果两行之间不空一行表示空格。
* 可以使用`<!-- -->` 进行注释。

***

## 小结

最近在Github上折腾博客，很多地方都用到了Markdown，在网上搜索了一些资料学习Markdown，顺便写了这篇介绍常用Markdown语法的文章。我觉得这篇文章介绍得还是有点细了，其实很多细节的地方我们一般用不到的，用到的时候再查也不迟。

不过，如果你觉得这些语法还不够用的话，可以阅读官方的文章：

* 中文版：[Markdown语法说明（详解版）](http://www.ituring.com.cn/article/504)
* 英文版：[Markdown: Syntax](http://daringfireball.net/projects/markdown/syntax)

中文版还有wowubuntu上的另一个版本，不过我觉得上面这个版本翻译得更好一些。

PS：BTW，虽然废话有点多，如果你跟我一样使用GitHub的话，我相信这篇翻译文章——[GitHub 风格的 Markdown 语法](https://github.com/cssmagic/blog/blob/master/github/github-flavored-markdown.md)会对你有帮助。

