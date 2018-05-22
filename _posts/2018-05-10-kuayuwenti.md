---
layout: post
title: 跨域
description: 
category: blog
---

产生跨域的根本原因是浏览器的同源策略。
同源是指，域名+协议+端口相同。

非同源带来的问题：
- Cookie、LocalStorage 和 IndexDB 无法获取。
- DOM 无法获得。
- AJAX 请求不能发送。

解决问题的方法有以下几种：

## 禁用浏览器安全策略
略

## jsonp
jsonp利用的是js脚本可以跨域的特性来实现跨域的。

基本实现原理：
- 在Head中动态添加一段javascript脚本，向服务端请求数据；
- 服务端收到带有callback（默认）参数的请求就认为是一个jsonp请求，将返回的数据封装在由callback参数指定的函数的参数中返回；
- 客户端解析后台返回的数据；
- 自动删除Head中的javascript脚本。

但jsonp有以下限制：
- 仅支持GET请求
- jsonp参数传递在URL中，存在安全隐患

## iframe跨域
通过设置document.domain来实现跨域。
常见应用场景是：网站对天气预报的显示。

## 服务器代理
大部分Web服务器，如Apache、Nginx等都支持配置白名单，即哪些网站是可以访问的。

## 中间层
将所有网站的请求都指向一个URL，由该URL进行请求转发，但遇到的问题是该URL在访问量很大的情况下容易产生性能瓶颈，考虑负载均衡。
