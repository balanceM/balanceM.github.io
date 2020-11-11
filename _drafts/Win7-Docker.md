---
id: 47
title: Win7 Docker
date: 2019-12-18T08:58:29+00:00
author: banana
layout: post
guid: http://wordpress.balancem.ltd/?p=47
permalink: /?p=47
categories:
  - Uncategorized
---
  * 保证VirtualBox能正常打开
  * <http://www.muxufang.com/a/813.html>
  * DockerQuickStart
  * 提示要下载最新.iso文件，这时候除非用代理，要不然很难下好。可以手动去相应github地址下好.iso文件，并放到对应文件夹下。C:\Users\Administrator.docker\machine\cache  
    C:\Program Files\Docker Toolbox
  * 
  * Hyper-v问题
  * <http://www.bubuko.com/infodetail-1642566.html> 

docker虚拟机ip地址获取： docker-machine ip

Docker ubuntu镜像更换apt-get源：

<pre class="wp-block-code"><code>RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean</code></pre>