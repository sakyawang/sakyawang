---
title: post请求执行window open
date: '2015-07-09'
description: window open新页面以post请求发送（url上不带参数）
categories:
-javascript

tags:
-javascript
-html

---
## 背景 ##
一般在html中打开新页面都是直接使用window.open(url)，打开新的页面是get请求，如果url有参数的话URL就会很长，在浏览器上会有参数显示。这里使用post请求可以避免该问题。

## 处理方案 ##

创建一个form表单method为post方式：

	<form action="" method="post" name="targetForm" id="targetForm" target="targetForm" onsubmit="openWindow('targetForm');">
		<input type="hidden" name="name1" id="id1"/>
		<input type="hidden" name="name2" id="id2"/>
	</form>

添加onsubmit事件，执行openWindow（），具体js函数如下：

	function openWindow(name){    
		window.open('about:blank',name);     
	}  

关键点是：

	onsubmit="openWindow('targetForm');"

中参数要是form表单的名字。

然后在操作的时候触发表单的提交事件：

$("#targetForm").submit();