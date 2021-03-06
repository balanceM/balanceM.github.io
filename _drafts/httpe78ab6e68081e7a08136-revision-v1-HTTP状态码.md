---
id: 37
title: HTTP状态码
date: 2019-12-11T08:11:27+00:00
author: banana
layout: revision
guid: https://wordpress.balancem.ltd/2019/12/11/36-revision-v1/
permalink: /2019/12/11/36-revision-v1/
---
#### [](https://github.com/bolasblack/http-api-guide#%E8%AF%B7%E6%B1%82%E6%88%90%E5%8A%9F)请求成功

  * 200&nbsp;**OK**&nbsp;: 请求执行成功并返回相应数据，如&nbsp;`GET`&nbsp;成功
  * 201&nbsp;**Created**&nbsp;: 对象创建成功并返回相应资源数据，如&nbsp;`POST`&nbsp;成功；创建完成后响应头中应该携带头标&nbsp;`Location`&nbsp;，指向新建资源的地址
  * 202&nbsp;**Accepted**&nbsp;: 接受请求，但无法立即完成创建行为，比如其中涉及到一个需要花费若干小时才能完成的任务。返回的实体中应该包含当前状态的信息，以及指向处理状态监视器或状态预测的指针，以便客户端能够获取最新状态。
  * 204&nbsp;**No Content**&nbsp;: 请求执行成功，不返回相应资源数据，如&nbsp;`PATCH`&nbsp;，&nbsp;`DELETE`&nbsp;成功

#### [](https://github.com/bolasblack/http-api-guide#%E9%87%8D%E5%AE%9A%E5%90%91)重定向

**重定向的新地址都需要在响应头&nbsp;`Location`&nbsp;中返回**

  * 301&nbsp;**Moved Permanently**&nbsp;: 被请求的资源已永久移动到新位置
  * 302&nbsp;**Found**&nbsp;: 请求的资源现在临时从不同的 URI 响应请求
  * 303&nbsp;**See Other**&nbsp;: 对应当前请求的响应可以在另一个 URI 上被找到，客户端应该使用&nbsp;`GET`&nbsp;方法进行请求。比如在创建已经被创建的资源时，可以返回&nbsp;`303`
  * 307&nbsp;**Temporary Redirect**&nbsp;: 对应当前请求的响应可以在另一个 URI 上被找到，客户端应该保持原有的请求方法进行请求

#### [](https://github.com/bolasblack/http-api-guide#%E6%9D%A1%E4%BB%B6%E8%AF%B7%E6%B1%82)条件请求

  * 304&nbsp;**Not Modified**&nbsp;: 资源自从上次请求后没有再次发生变化，主要使用场景在于实现[数据缓存](https://github.com/bolasblack/http-api-guide#user-content-%E6%95%B0%E6%8D%AE%E7%BC%93%E5%AD%98)
  * 409&nbsp;**Conflict**&nbsp;: 请求操作和资源的当前状态存在冲突。主要使用场景在于实现[并发控制](https://github.com/bolasblack/http-api-guide#user-content-%E5%B9%B6%E5%8F%91%E6%8E%A7%E5%88%B6)
  * 412&nbsp;**Precondition Failed**&nbsp;: 服务器在验证在请求的头字段中给出先决条件时，没能满足其中的一个或多个。主要使用场景在于实现[并发控制](https://github.com/bolasblack/http-api-guide#user-content-%E5%B9%B6%E5%8F%91%E6%8E%A7%E5%88%B6)

#### [](https://github.com/bolasblack/http-api-guide#%E5%AE%A2%E6%88%B7%E7%AB%AF%E9%94%99%E8%AF%AF)客户端错误

  * 400&nbsp;**Bad Request**&nbsp;: 请求体包含语法错误
  * 401&nbsp;**Unauthorized**&nbsp;: 需要验证用户身份，如果服务器就算是身份验证后也不允许客户访问资源，应该响应&nbsp;`403 Forbidden`&nbsp;。如果请求里有&nbsp;`Authorization`&nbsp;头，那么必须返回一个&nbsp;[`WWW-Authenticate`](https://tools.ietf.org/html/rfc7235#section-4.1)&nbsp;头
  * 403&nbsp;**Forbidden**&nbsp;: 服务器拒绝执行
  * 404&nbsp;**Not Found**&nbsp;: 找不到目标资源
  * 405&nbsp;**Method Not Allowed**&nbsp;: 不允许执行目标方法，响应中应该带有&nbsp;`Allow`&nbsp;头，内容为对该资源有效的 HTTP 方法
  * 406&nbsp;**Not Acceptable**&nbsp;: 服务器不支持客户端请求的内容格式，但响应里会包含服务端能够给出的格式的数据，并在&nbsp;`Content-Type`&nbsp;中声明格式名称
  * 410&nbsp;**Gone**&nbsp;: 被请求的资源已被删除，只有在确定了这种情况是永久性的时候才可以使用，否则建议使用&nbsp;`404 Not Found`
  * 413&nbsp;**Payload Too Large**&nbsp;:&nbsp;`POST`&nbsp;或者&nbsp;`PUT`&nbsp;请求的消息实体过大
  * 415&nbsp;**Unsupported Media Type**&nbsp;: 服务器不支持请求中提交的数据的格式
  * 422&nbsp;**Unprocessable Entity**&nbsp;: 请求格式正确，但是由于含有语义错误，无法响应
  * 428&nbsp;**Precondition Required**&nbsp;: 要求先决条件，如果想要请求能成功必须满足一些预设的条件

#### [](https://github.com/bolasblack/http-api-guide#%E6%9C%8D%E5%8A%A1%E7%AB%AF%E9%94%99%E8%AF%AF)服务端错误

  * 500&nbsp;**Internal Server Error**&nbsp;: 服务器遇到了一个未曾预料的状况，导致了它无法完成对请求的处理。
  * 501&nbsp;**Not Implemented**&nbsp;: 服务器不支持当前请求所需要的某个功能。
  * 502&nbsp;**Bad Gateway**&nbsp;: 作为网关或者代理工作的服务器尝试执行请求时，从上游服务器接收到无效的响应。
  * 503&nbsp;**Service Unavailable**&nbsp;: 由于临时的服务器维护或者过载，服务器当前无法处理请求。这个状况是临时的，并且将在一段时间以后恢复。如果能够预计延迟时间，那么响应中可以包含一个&nbsp;`Retry-After`&nbsp;头用以标明这个延迟时间（内容可以为数字，单位为秒；或者是一个&nbsp;[HTTP 协议指定的时间格式](http://tools.ietf.org/html/rfc2616#section-3.3)）。如果没有给出这个&nbsp;`Retry-After`&nbsp;信息，那么客户端应当以处理 500 响应的方式处理它。

`501`&nbsp;与&nbsp;`405`&nbsp;的区别是：`405`&nbsp;是表示服务端不允许客户端这么做，`501`&nbsp;是表示客户端或许可以这么做，但服务端还没有实现这个功能