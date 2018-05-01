---
layout: post
title: CSS 定位与布局
description: 
category: blog
---

> 引用 [css布局](https://segmentfault.com/a/1190000011358507)

#### 定位
- static：默认定位 **平面元素**
- fixed：相对定位，相对浏览器定位，固定定位。(上浮层、不占用原层位置)
应用场景：网页固定位置显示站点的联系方式等
- relative：相对定位，相对非static的父容器定位。(上浮层、原层位置保留但元素上浮) 
- absulute：绝对定位，相对非static的父容器定位。（上浮层，不占据原层空间的整体上浮），其他元素可以占据该元素在原层的空间。
- sticky：随网页上下移动，但滚动条下拉到一定位置后，该元素位置不变。
- inherit: 继承
- float：类似于absulute，浮动定位。应用场景：菜单栏的显示

难点：
- relative \ absulute： 找准定位的原点，非static的左上角开始定位，而fixed定位是相对于浏览器定位的。
- 定位时一般配合 left top 使用。
- 特别注意：应用float定位的div，其他地方需要清除浮动效果，否则可能会引起排版混乱。

#### 元素位置
- 块级元素：矩形框，会自动撑满区域空间   

说明：{ width: auto }默认 占满宽度，但{ height: auto }默认占据 很小的高度 的原因是：auto 表示浏览器自动计算，但自动计算一般有一个基准值，由于一般浏览器都是允许上下滚动的，所以浏览器找不到垂直方向的基准，故宽度设置为auto时，会使内部元素的长度自动填充满父元素的width，但高度设置为auto时，仅占据很小的高度。

- 行内元素：一个或多个行框

注意：偏移量对static的元素不起作用。

#### 布局

盒子模型  margin \ border \ padding \ content

box-sizing有两种方式：
- content-size ：width设置的是content宽度，计算元素的宽度时需要加上 margin + border + padding 的值。 
- border-size ：width设置的是border宽度 = border + padding + content 值。

#### 字体
字体大小  px \ % \ em \ rem
- px 像素 显示器一个小黑点就是一个像素）
- % 百分比 (相对父容器 )
- em 参考父容器 (相对父容器)  如：父容器 font-size：20px ，那么子元素 1em = 20px
- rem 参考body (相对body)  如：body设置 font-size: 30px ，那么元素 1rem = 30px 

#### 演变
- table 布局： 不灵活，不好看
- div+css 布局: 沿用至今

