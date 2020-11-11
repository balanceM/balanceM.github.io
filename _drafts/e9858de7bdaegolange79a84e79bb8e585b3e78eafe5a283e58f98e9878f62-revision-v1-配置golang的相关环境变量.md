---
id: 63
title: 配置golang的相关环境变量
date: 2020-01-06T15:51:43+00:00
author: banana
layout: revision
guid: https://wordpress.balancem.ltd/2020/01/06/62-revision-v1/
permalink: /2020/01/06/62-revision-v1/
---
<pre class="wp-block-code"><code>配置golang的相关环境变量
默认go 安装的文件地址是 /usr/local/Cellar/go/

go的配置写入环境
vim .bash_profile

将下面内容添加进上面的文件
#GO
#GOROOT
export GOROOT=/usr/local/Cellar/go/1.12.3/libexec
#GOPATH
export GOPATH=$HOME/Documents/code/go
#Bin
export PATH=${PATH}:$GOPATH/bin</code></pre>