---
id: 64
title: mac使用
date: 2020-01-06T15:53:42+00:00
author: banana
layout: revision
guid: https://wordpress.balancem.ltd/2020/01/06/29-revision-v1/
permalink: /2020/01/06/29-revision-v1/
---
**ruby的安装**

尽管brew工具可以安装ruby，但是在默认ruby的使用，相应的gem的使用控制上。  
使用类似于**rvm 或 rbenv** 这样的ruby版本控制工具安装ruby才是使用最简单的选择，省去了很多不必要的麻烦。

**git代理**

代理对 ssh 协议是无效的：git clone git@github.com:xxxxxx/xxxxxx.git  
此时，用 git clone https://github.com:xxxxxx/xxxxxx.git 才能利用代理进行加速

**快捷键**

显示隐藏文件：`commond + shift+ .`