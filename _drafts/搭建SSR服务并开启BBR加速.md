---
id: 56
title: 搭建SSR服务并开启BBR加速
date: 2019-12-27T03:05:52+00:00
author: banana
layout: post
guid: http://wordpress.balancem.ltd/?p=56
permalink: /?p=56
categories:
  - Uncategorized
---
### 前言 {#前言}

一键搭建shadowsocks/搭建shadowsocksR的shell脚本，一键脚本适用[Vultr](https://www.vultr.com/)上的和[搬瓦工](https://www.bwgyhw.cn/)所有机型（CentOS、Ubuntu、Debian），搭建ss服务器支持所有客户端类型，本机你是iOS，Android，Windows，Mac，或者是Linux，搭建ss/ssr都是适用的科学上网方式。一键脚本搭建SS/SSR服务器，绝对没有任何问题，任何问题欢迎留言。一键脚本内容包括一键搭建shadowsocks/一键搭建shadowsocksR+一键开启bbr加速，适合新手小白。

### 一键搭建shadowsocksR {#一键搭建shadowsocksr}

再次提醒，如果安装了SS，就不需要再安装SSR了，如果要改装SSR，请按照上一部分内容的教程先卸载SS！！！

  1. 下载一键搭建ssr脚本`1    git clone https://github.com/balanceM/ss-fly` 
  2. 运行搭建ssr脚本代码`1  ss-fly/ss-fly.sh -ssr` 
  3. 输入对应的参数 执行完上述的脚本代码后，会进入到输入参数的界面，包括服务器端口，密码，加密方式，协议，混淆。可以直接输入回车选择默认值，也可以输入相应的值选择对应的选项.

全部选择结束后，会看到如下界面，就说明搭建ssr成功了：

<pre class="wp-block-code"><code>
Congratulations, ShadowsocksR server install completed!
Your Server IP        :你的服务器ip
Your Server Port      :你的端口
Your Password         :你的密码
Your Protocol         :你的协议
Your obfs             :你的混淆
Your Encryption Method:your_encryption_method
 
Welcome to visit:https://shadowsocks.be/9.html
Enjoy it!
</code></pre>

  1. 相关操作ssr命令  
     `启动：/etc/init.d/shadowsocks start  停止：/etc/init.d/shadowsocks stop  重启：/etc/init.d/shadowsocks restart  状态：/etc/init.d/shadowsocks status  配置文件路径：/etc/shadowsocks.json  日志文件路径：/var/log/shadowsocks.log  代码安装目录：/usr/local/shadowsocks` 
  2. 卸载ssr服务`1  ./shadowsocksR.sh uninstall`

### 一键开启BBR加速 {#一键开启bbr加速}

BBR是Google开源的一套内核加速算法，可以让你搭建的shadowsocks/shadowsocksR速度上一个台阶，本一键搭建ss/ssr脚本支持一键升级最新版本的内核并开启BBR加速。

BBR支持4.9以上的，如果低于这个版本则会自动下载最新内容版本的内核后开启BBR加速并重启，如果高于4.9以上则自动开启BBR加速，执行如下脚本命令即可自动开启BBR加速：

<pre class="wp-block-code"><code>1
ss-fly/ss-fly.sh -bbr
</code></pre>

装完后需要重启系统，输入y即可立即重启，或者之后输入`reboot`命令重启。

判断BBR加速有没有开启成功。输入以下命令：

<pre class="wp-block-code"><code>1
sysctl net.ipv4.tcp_available_congestion_control
</code></pre>

如果返回值为：

<pre class="wp-block-code"><code>
net.ipv4.tcp_available_congestion_control = bbr cubic reno
</code></pre>

后面有bbr，则说明已经开启成功了。

### 声明 {#声明}

本文只作为技术分享，请遵守相关法律，严禁做违法乱纪的事情！