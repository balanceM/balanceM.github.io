---
id: 72
title: docker in Window
date: 2020-06-11T03:01:49+00:00
author: banana
layout: revision
guid: http://wordpress.balancem.ltd/2020/06/11/70-revision-v1/
permalink: /2020/06/11/70-revision-v1/
---
docker-machine default start  
启动default的docker虚拟机  
  
docker-machine ip default  
查看default虚拟机的ip地址  
  
docker ps -a  
列出所有的容器  
  
docker container ls  
列出正在运行的容器  
  
docker image ls  
列出镜像  
docker image -a  
列出镜像（包括基础镜像）  
  
docker rm (容器id)  
删除指定的容器； -f参数，强制删除正在运行的容器。  
docker rmi (镜像id)  
删除指定的镜像  
  
eg.  
docker build -t filemanager .  
构建 镜像  
docker run -d &#8211;name filemanagerC -p 8080:3000 filemanager  
创建镜像 filemanager 的容器 filemanagerC,  
虚拟主机端口8080映射到容器服务的端口3000上。  
**访问：  
（ default虚拟机的ip地址 ）：8080**