---
id: 76
title: wordpress域名到期
date: 2020-09-15T09:46:54+00:00
author: banana
layout: revision
guid: http://180.76.187.186/2020/09/15/74-revision-v1/
permalink: /2020/09/15/74-revision-v1/
---
wordpress域名到期后，出现文件地址引用错误，URL跳转会使用之前的域名地址进行跳转，导致找不到页面的错误，想直接改为IP地址使用。  
**解决方法**：  
修改wordpress数据库的wp_options表,  
siteurl的值改为服务器ip(:port)地址,  
home的值改为服务器ip(:port)地址。  
**code**:  
mysql -uroot -p ;  
use wordpress;  
update wp\_options set option\_value=&#8221;http://1\*\*.\*\*.\*\\*\*.\*\**&#8221; where option_name = &#8220;siteurl&#8221;;  
update wp\_options set option\_value=&#8221;http:// 1\*\*.\*\*.\*\\*\*.\*\** &#8221; where option_name = &#8220;home&#8221;;