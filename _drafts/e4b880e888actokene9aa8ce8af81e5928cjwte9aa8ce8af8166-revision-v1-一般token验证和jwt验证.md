---
id: 68
title: 一般token验证和jwt验证
date: 2020-04-26T03:07:26+00:00
author: banana
layout: revision
guid: https://wordpress.balancem.ltd/2020/04/26/66-revision-v1/
permalink: /2020/04/26/66-revision-v1/
---
**一般token验证流程**：  
1. 客户端将用户的用户名和密码发送到服务器  
2. 服务器校验成功后，生成token令牌，存于数据库，并发送给客户端  
3. 客户端保存token， 请求资源时，在http协议的请求头中带上token去访问服务器  
4. 服务端进行token校验，成功后返回资源。  
**特点**：  
客户端每次都要携带token, 客户端的内容比较多 



**jwt验证流程**：  
组成: **header，payload，signature**  
1. 在头部信息中声明加密算法和常量， 然后把header使用json转化为字符串  
2. 在载荷中声明用户信息和一些其他内容，再次使用json把载荷部分转化为字符串  
3. 使用header上声明的加密算法和项目随机生成的secret，将1和2生成的字符串进行加密，生成新的字符串。  
4. 解密的时候，客服端带着jwt发送请求，服务器使用secret进行解密得到信息。  
**特点**：  
1. 将头部与载荷进行字符串转化  
2. 解密时，不访问数据库，使用secret  
3. secret不可泄密