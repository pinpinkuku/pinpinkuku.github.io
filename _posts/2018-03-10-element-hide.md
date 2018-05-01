---
layout: post
title: CSS 隐藏元素的几种方式对比
description: 
category: blog
---

#### CSS隐藏元素常见方法

##### **display: none**
元素彻底从页面上消失，元素占用的空间会被其他元素占有，会导致浏览器的重排和重绘。
事件触发：不会触发(设置 $('.none').click() 除外)。
transition影响： 完全不受影响，元素立即消失。

##### **visibility: hidden**
元素从页面上消失，其占有的空间会保留，会导致浏览器重绘，但不会导致浏览器重排。
应用场景：适用于元素隐藏后不希望页面布局发生变化的场景。
事件触发：不会触发(设置 $('.none').click() 除外)。
transition影响： 元素消失事件与transition属性设置的时间一致，但没有动画效果。

##### **opacity: 0**
opacity： 设置元素透明度，当值为0时，元素在用户看来是隐藏的。
事件触发：可以触发。
transition影响： 能进行正常的动画效果。

##### **设置盒模型属性为0**
将元素的margin, border, padding, height, width等设置为0，存在子元素或内容时，还需设置overflow: hidden 来隐藏子元素；
说明：这类方式不实用且存在问题，但jquery的slideUp动画就是通过这类方式来实现的。
事件触发：据情况分析，若全部属性均设置为0时不会触发，若border, padding等属性不为0时，可以触发事件。(设置 $('.none').click() 除外)。
transition影响： 能进行正常的动画效果。

``` css
.hiddenBox {
    margin: 0;
    border: 0;
    padding: 0;
    height: 0;
    width: 0;
    overflow: hidden;
}
```

##### **总结**
- 隐藏元素不会触发事件的真实原因是：鼠标无法真正接触到被设置成隐藏的元素。
- 最常用的隐藏方式还是 display: none 和 visibility: hidden，其他的仅仅是一些巧计。