---
id: 28
title: Chrome Extension error
date: 2019-12-04T09:43:31+00:00
author: banana
layout: revision
guid: https://wordpress.balancem.ltd/2019/12/04/25-revision-v1/
permalink: /2019/12/04/25-revision-v1/
---
<p class="has-small-font-size">
  <a href="https://stackoverflow.com/questions/38457208/chrome-extension-error-unchecked-runtime-lasterror-while-running-browseraction">Chrome Extension error: “Unchecked runtime.lastError : Icon invalid.</a>
</p>

<p class="has-small-font-size">
  <strong>解决</strong>：<br />chrome.browserAction.setIcon方法的参数path，icon图片的像素要求是 19*19px, 38*38px, 16*16px。其他像素就会报此类错误。
</p>

3种存储数据方式：

**localStorage**： 受域的限制，数据只能再一个域里共享。想突破域的限制，可以通过向background sendMessage 发送接收数据的方式间接得到数据  
**chrome 存储API**：  
StorageArea 设为sync时，chrome可以通过登陆的账户自动同步数据，未登录账户时，和设为local没区别。相较于localStorage，没有域的限制，速度更快，可以保存对象类型。  
**Web SQL Database**：  
将数据存储于客户端数据库， 三个核心方法`openDatabase`、`transaction`和`executeSql`