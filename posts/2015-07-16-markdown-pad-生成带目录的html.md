---
title: markdown pad 生成带目录的html
date: '2015-07-16'
description: 使用markdown pad生成带目录的html
categories:
-markdown
tags:
-markdown
-config

---
## 环境
win7、markdown pad 2

## 目的

使用markdown pad 2编辑生成wiki风格的接口文档

## 处理方案

使用markdown pad 2的导出功能和高级设置的Html head 编辑器功能。

* 工具-->选项-->高级-->Html head 编辑器

![html head 编辑器](http://7xj99v.com1.z0.glb.clouddn.com/markdownpadconfig.png)

* 打开编辑器

输入：

	<script>
		document.addEventListener("DOMContentLoaded", function() {
		    // 生成目录列表
		    var outline = document.createElement("ul");
		    outline.setAttribute("id", "outline-list");
		    outline.style.cssText = "border: 1px solid #ccc;";
		    document.body.insertBefore(outline, document.body.childNodes[0]);
		    // 获取所有标题
		    var headers = document.querySelectorAll('h1,h2,h3,h4,h5,h6');
		    for (var i = 0; i < headers.length; i++) {
		        var header = headers[i];
		        var hash = _hashCode(header.textContent);
		        // MarkdownPad2无法为中文header正确生成id，这里生成一个
		        header.setAttribute("id", header.tagName + hash);
		        // 找出它是H几，为后面前置空格准备
		        var prefix = parseInt(header.tagName.replace('H', ''), 10);
		        outline.appendChild(document.createElement("li"));
		        var a = document.createElement("a");
		        // 为目录项设置链接
		        a.setAttribute("href", "#" + header.tagName + hash)
		        // 目录项文本前面放置对应的空格
		        a.innerHTML = new Array(prefix * 4).join('&nbsp;') + header.textContent;
		        outline.lastChild.appendChild(a);
		    }
		 
		});
	 
		// 类似Java的hash生成方式，为一段文字生成一段基本不会重复的数字
		function _hashCode(txt) {
		     var hash = 0;
		     if (txt.length == 0) return hash;
		     for (i = 0; i < txt.length; i++) {
		          char = txt.charCodeAt(i);
		          hash = ((hash<<5)-hash)+char;
		          hash = hash & hash; // Convert to 32bit integer
		     }
		     return hash;
		}
	</script>

保存

* 测试效果

**新建test.md编辑：**
	
	## 标题1
	标题1内容
	### 标题11
	标题11内容
	### 标题12
	标题12内容
	## 标题2
	标题2内容
	### 标题21
	标题21内容
	### 标题22
	标题22内容
	## 标题3
	标题3内容
	### 标题31
	标题31内容
	### 标题32
	标题32内容

**导出html文件**

![导出html文件](http://7xj99v.com1.z0.glb.clouddn.com/export.png)

**查看html文件**

![查看html](http://7xj99v.com1.z0.glb.clouddn.com/html.png)
	



