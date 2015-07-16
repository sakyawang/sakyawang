---
title: 使用sublime text2 编辑markdown文件并导出带目录的html
date: '2015-07-16'
description: 使用sublime text 2 配置markdown高亮显示，导出带目录的html
categories:
-markdown
-sublime
tags:
-markdown
-sublime

---
前一篇文章介绍了使用markdown pad2来生成带目录的html文件。但是有很多程序员喜欢使用sublime来进行markdown的编写。这里介绍一下sublime下如何把markdown文件生成带目录的html。

## 环境 ##

win7、 sublime text2

## 配置过程 ##

**sublime text 安装 markdown preview插件**

sublime text 安装插件基本配置请参看之前的一篇文章：

[sublime text2 安装插件](http://sakyawang.github.io/sublime/sublime-text2-%E5%AE%89%E8%A3%85%E6%8F%92%E4%BB%B6/)

ctrl+shift+P 调出窗口，输入 install package --> 输入 markdown preview 选中安装插件。

**配置markdown高亮显示**

在Preferences ->Package Settings->Markdown Preview->Setting Default中找到

	"enable_mathjax": true,

    /*
        Enable uml support scripts: flowchart.js and sequence-diagram.js.
    */
    "enable_uml": false,

    /*
        Enable highlighting. This enables codehilite extension if not already enabled.
    */
    "enable_highlight": true,

enable_mathjax 和 enable_highlight设置为true。

## 编写markdown输出带目录的html ##

新建test.md文件，输入测试内容：

	[TOC]
	# 标题 #
	## 标题1 ##
	
	标题1内容
	
	### 标题11 ###
	
	标题11内容
	
	### 标题12 ###
	
	标题12内容
	 
	## 标题2 ##
	
	标题2内容
	
	### 标题21 ###
	
	标题21内容
	
	### 标题22 ###
	
	标题22内容
	
	## 标题3 ##
	
	标题3内容
	
	### 标题31 ###
	
	标题31内容
	
	### 标题32 ###
	
	标题32内容

配置markdown preview编译生成html文件，如下：

![配置markdown编译](http://7xj99v.com1.z0.glb.clouddn.com/sublimeconfig.png)

执行ctrl + B编译markdown为html

![编译markdown](http://7xj99v.com1.z0.glb.clouddn.com/buildmarkdown.png)

打开test.html查看效果

![效果](http://7xj99v.com1.z0.glb.clouddn.com/testhtml.jpg)

***关键点是在要生成目录的位置添加[TOC]***


