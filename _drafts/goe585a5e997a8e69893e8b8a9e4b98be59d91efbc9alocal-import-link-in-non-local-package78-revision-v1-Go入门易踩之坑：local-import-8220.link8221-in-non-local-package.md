---
id: 83
title: 'Go入门易踩之坑：local import &#8220;./link&#8221; in non-local package'
date: 2020-09-22T09:28:31+00:00
author: banana
layout: revision
guid: http://180.76.187.186/2020/09/22/78-revision-v1/
permalink: /2020/09/22/78-revision-v1/
---
<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="http://180.76.187.186/wp-content/uploads/2020/09/image.png" alt="" class="wp-image-79" /><figcaption>目录结构</figcaption></figure>
</div>

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="http://180.76.187.186/wp-content/uploads/2020/09/image-1.png" alt="" class="wp-image-80" srcset="http://180.76.187.186/wp-content/uploads/2020/09/image-1.png 374w, http://180.76.187.186/wp-content/uploads/2020/09/image-1-300x206.png 300w" sizes="(max-width: 374px) 100vw, 374px" /><figcaption>link/link.go</figcaption></figure>
</div>

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="http://180.76.187.186/wp-content/uploads/2020/09/image-2.png" alt="" class="wp-image-81" srcset="http://180.76.187.186/wp-content/uploads/2020/09/image-2.png 376w, http://180.76.187.186/wp-content/uploads/2020/09/image-2-300x216.png 300w" sizes="(max-width: 376px) 100vw, 376px" /><figcaption>main.go</figcaption></figure>
</div>

问题根本原因就是命令go mod init app 和代码 import &#8220;./link&#8221; 不对应。引用本地模块的引用方法是 import &#8220;module/path&#8221;，也就是说如果用了go mod init app命令，代码引用本地模块就需是import &#8220;app/link&#8221;。注意module名和工程所在文件夹名无必然关联