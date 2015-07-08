---
title: sublime text2 安装插件
date: '2015-07-08'
description: sublime text2 配置安装插件
categories:
-sublime

tags:
-sublime
-config

---
sublime tex t2本身自带了编程语言雷插件，可以通过Preferences-->Browse Packages查看。
当然还有一些方便开发的插件需要单独安装。这里说一下sublime text2安装插件的操作流程。

## 环境 ##

win7、sublime text2

## 配置 ##

打开sublime 使用ctrl+` 调出控制台窗口，输入：

	import urllib2,os; 
	pf='Package Control.sublime-package'; 
	ipp=sublime.installed_packages_path(); 
	os.makedirs(ipp) 
	if not 
		os.path.exists(ipp) 
	else 
		None; 
	urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler()));
	open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); 
	print 'Please restart Sublime Text to finish installation'

执行完毕之后，重启sublime。

## 安装插件 ##

ctrl+shift+P调出功能搜索框，输入 install 选择 install package，然后查找自己喜欢的插件 选择安装。

