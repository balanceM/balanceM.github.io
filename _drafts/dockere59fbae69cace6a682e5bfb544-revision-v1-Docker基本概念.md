---
id: 46
title: Docker基本概念
date: 2019-12-11T16:39:01+00:00
author: banana
layout: revision
guid: https://wordpress.balancem.ltd/2019/12/11/44-revision-v1/
permalink: /2019/12/11/44-revision-v1/
---
**镜像  
** 一个特殊的文件系统， 提供容器运行时所需的程序、库、资源、配置等文件 。  
还包括，为运行时准备的一些配置参数（如匿名卷、环境变量、用户等）  
没有动态数据，构建之后，内容不可变

**容器**  
镜像的“实例”， 是镜像运行时的实体  
本质是 运行在一个隔离的环境的进程。（有独立的root文件系统，网络配置，进程空间，用户ID空间）

**仓库服务**（Docker Registry）  
一个可以让镜像存储，分发的地方（服务）。  
Docker镜像服务包含很多仓库（Repository），每个仓库放着不同版本（标签）的镜像。  
eg. `ubuntu`仓库有 `ubuntu：16.04` ， `ubuntu:18.04` 等镜像  
公开服务 ：  
国际上有， <a rel="noreferrer noopener" href="https://hub.docker.com/" target="_blank">Docker Hub</a> <a rel="noreferrer noopener" href="https://quay.io/repository/" target="_blank">Quay.io</a>  <a rel="noreferrer noopener" href="https://cloud.google.com/container-registry/" target="_blank">Google Container Registry</a>  
Docker Hub 镜像服务加速， <a rel="noreferrer noopener" href="https://cr.console.aliyun.com/#/accelerator" target="_blank">阿里云加速器</a>、<a rel="noreferrer noopener" href="https://www.daocloud.io/mirror#accelerator-doc" target="_blank">DaoCloud 加速器</a>   
国内有，  <a rel="noreferrer noopener" href="https://hub.tenxcloud.com/" target="_blank">时速云镜像仓库</a>、<a rel="noreferrer noopener" href="https://c.163.com/hub#/m/library/" target="_blank">网易云镜像服务</a>、<a rel="noreferrer noopener" href="https://hub.daocloud.io/" target="_blank">DaoCloud 镜像市场</a>、<a rel="noreferrer noopener" href="https://cr.console.aliyun.com/" target="_blank">阿里云镜像库</a>