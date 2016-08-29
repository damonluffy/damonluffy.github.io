---
layout:     post
title:      "https下http链接失效"
subtitle:   " \"无法正常显示Font Awesome图标\""
date:       2016-07-29 12:00:00
author:     "damonluffy"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - https & http
---

> “hybrid is not always good. ”

fork 自Hux 的git pages 无法正常显示font awesome 的图标，通过F12可以查看到mixed context block issue, 

Blocked loading mixed active content "http://xxx-static.com/js/lib/jquery-1.4.2.min.js"


看来是script 链接被屏蔽了。经过调查，发现原来是测试用的Firefox浏览器Version23里面有个新特性：

security.mixed_content.block_active_content默认值被设置为True了

这样，在HTTPS的网页中，如果引用了HTTP的资源，就会出错。

git pages 在不配置自己的域名的情况下就只能用https了，要么申请一个域名，要么找到https的cdn。

 
解决方式：

1，浏览器端，使用about:config，打开属性面板，设置该属性为False即可。

2，当然，不可能要求每个用户都去修改浏览器设置，所以我们在引用资源的时候，特别是一些共用资源，对其协议要心中有数。

一般情况下，使用“//xxx-static.com/js/lib/jquery-1.4.2.min.js”的格式，不指定其协议，自动采用和页面相同的协议来引用资源了。