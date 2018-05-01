---
layout: post
title: HTML 块级元素和行内元素
description: 
category: blog
---

#### 块级元素和行内元素的区别
- 块级元素独占一行，其宽度自动填满父元素宽度，而行内元素不会独占一行，相邻行内元素会排列在同一行中，其宽度随元素的内容而变化。
- 一般情况下，块级元素可以设置width、height属性，而行内元素设置width,height无效
- 块级元素可以设置margin和padding，而行内元素竖直方向无效
- 块级元素可以包含块级元素和行内元素，但行内元素能包含行内元素，不能包含块级元素

#### 常见的块级元素
``` html
<address>...</address>
<center>...</center>
<h1>...</h1> 标题 1 ~ 6 级
<hr>
<p>...</p>
<pre>...</pre>
<blockquote>...</blockquote>
<marquee>...</marquee>
<ul>...</ul>
<ol>...</ol>
<dl>...</dl>
<table>...</table>
<form>...</form>
<div>...</div>
```

#### 常见的行内元素
``` html
<span>...</span>
<a>...</a>
<br>
<b>...</b>
<strong>...</strong>
<img>
<sup>...</sup>
<sub>...</sub>
<i>...</i>
<em>...</em>
<del>...</del>
<u>...</u>
<input>...</input>
<textarea>...</textarea>
<select>...</select>
```