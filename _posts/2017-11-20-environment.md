---
layout: post
title: bash配置文件的区别
date: 2017-3-02
categories: blog
tags: [Linux]
description: 
---
全局  
/etc/profile 此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行，并从/etc/profile.d目录的配置文件中搜集shell的设置  
/etc/profile.d/×.sh #export PATH="/usr/local/apache/bin:$PATH"  
/etc/bashrc 为每一个运行bash shell的用户执行此文件,当bash shell被打开时,该文件被读取  

个人  
~/.bash_profile 每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该文件仅仅执行一次!默认情况下,他设置一些环境变量,执行用户的.bashrc文件  
~/.bashrc 该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该文件被读取  
~/.bash_logout 当每次退出系统(退出bash shell)时,执行该文件  


	~/.bashrc等中设定的变量(局部)只能继承 /etc/profile 中的变量,他们是"父子"关系.

用户登录后加载配置文件的顺序：
1./etc/profile-------->/etc/profile.d/*.sh  
2.~/.bash_profile-------->~/.bashrc---------->/etc/bashrc  

	说明：
	bash首先执行 /etc/profile 脚本，/etc/profile 脚本先依次执行 /etc/profile.d/*.sh
	随后bash会执行 ～/.bash_profile 脚本, ～/.bash_profile脚本会执行～/.bashrc脚本,而～/.bashrc脚本会执行/etc/bashrc脚本
	至此,所有的环境变量和初始化设定都已经加载完成
	bash随后会调用terminfo和inputrc，分别完成终端属性和键盘映射的设定

which #在当前登录用户的PATH环境变量中查找某个命令的完整路径









