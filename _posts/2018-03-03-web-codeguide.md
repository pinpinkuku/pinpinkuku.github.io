---
layout: post
title: 前端编码规范
description: 命令规则、HTML、CSS、JS
category: blog
---

# **命名规范**
坚持使用好的代码规范，无论团队人数多少，代码风格应该一致

> 引用 [Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/)

## **命名规则**

- 项目命名：全部采用小写方式，以下划线为分割，如：my_project_name
- 目录命名：参照项目命名规则，有复数时，要使用复数，如：
scripts, styles, images
- js文件命名：参照项目命名规则，如account_model.js
- css文件命名：参照项目命名规则，如retina_sprites.scc
- HTML文件命名：参照项目命名规则，如error_report.html

## **HTML**
### **语法**
- 缩进使用soft tab（4个空格）；
- 嵌套的节点应该缩进；
- 属性使用双引号；
- 属性名全小写，用 _ 做分割符；
- 不要忽略可选的关闭标签；
- 不要再自动闭合的标签使用斜线；  
如：
``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Page title</title>
    </head>
    <body>
        <img src="pic/apple.jpg" alt="apple">

        <h1 class="Hello_world">Hello World!</h1>
    </body>
</html>
```

### **基本**
- doctype大写；
- 加上lang属性；
- 字符编码通常用'UTF-8';
- 用<meta>标签指定页面用什么版本的IE来渲染

如：  
``` html
<!DOCTYPE html>
<html lang="en-us">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    </head>
</html>
```

### **属性顺序**
属性应该按特定的顺序出现以保证易读性：
- class
- id
- name
- data-*
- src, for, type, href, value, max-length, max, min, pattern
- placeholder, title, alt
- aria-*, role
- required, readonly, disabled  

class是为高可复用组件设计的，所以应处于第一位；
id更加具体且应该尽量少用，所以將它放在第二位；  
如：  
``` html
<a class="..." id="..." data-model="abc" href="#">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### **其他**
- 应尽量避免在JS文件中生成标签，会导致内容难以查找、编辑且性能也会更差；
- 减少标签数量，应尽量避免多余的父节点，可通过迭代和重构来使html变得更少；
- 实用高于完美，任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

## **CSS, SCSS**
### **语法**
- 缩进使用Soft tabl(4个空格)
- 每个属性声明末尾都要加分号；  

如：
``` css
.element{
    position: absolute;
    top: 10px;
    left: 10px;

    border-radius: 10px;
    width: 50px;
    height: 50px;
}
```

### **空格**
以下情况不需要空格：
- 属性名后
- 多个规则的分隔符','前
- !important '!'后
- 属性值中'('和')'前
- 行末不要有多余的空格  

以下情况需要空格：
- 属性前
- 选择器'>', '+', '~'前后
- '{'前
- !important '!'前
- @else前后
- 属性值中的','后
- 注释'/*'后和'*/'前  

### **注释**
- 统一用'/* */'进行注释；
- 缩进与下一行代码保持一致；
- 可位于一个代码行的末尾，与代码间隔一个空格；

### **引号**
- 最外层统一使用双引号；
- url的内容要用引号；
- 属性选择器中的属性值需要引号；

### **命名**
- 类名使用小写字母，以中划线分隔；
- id采用驼峰命名法；
- scss中的变量、函数、混合、placeholder采用驼峰命名法；

### **属性声明顺序**

### **其他**
- 不允许有空的规则；
- 元素选择器用小写字母；
- 去掉小数点前面的0；
- 去掉数据中不必要的小数点和末尾的0；
- 属性值'0'后面不要加单位；
- 同个属性不同前缀的写法需要在垂直方向保持对其；
- 无前缀的标准属性应该写在有前缀的属性后面；
- 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；
- 不要在一个文件里出现两个相同的规则；
- 用border: 0; 代替 border: none; ;
- 选择器不要超过4层；
- 发布的代码中不要有 @import ;
- 尽量少用'*'选择器；

## **JavaScript**

### **语法**
- 缩进使用 soft tab（4个空格）；
- 单行长度不要超过80；
- 最外层统一使用单引号；
- 一个函数作用域中的所有变量声明尽量提到函数首部，用一个var声明，不允许出现两个连续的var声明；  

如：
``` javascript
var x = 1,
    y = 'foo',
    z = '<div id="test"></div>';

if (x < y) {
    x += 10;
} else {
    x += 1;
}
```

### **分号**
需要加分号的情况：
- 变量声明
- 表达式
- return
- throw
- break
- continue
- do-while

如：
``` javascript
var x = 1;

x++;

do {
    x++;
} while(x < 10);
``` 

### **空格**
不需要加空格的情况：
- 对象的属性名后
- 前缀一元运算符后，后缀一元运算符前
- 函数调用括号前
- 声明函数或函数表达式 '('前不要空格
- 数组的'['后和']'前
- 对象的'{'后和'}'前
- 运算符'('后和')'前  

需要加空格的情况：
- 二元运算符前后
- 三元运算符 '?:'前后
- 代码块'{'前
- 以下关键字前：else, while, catch, finally
- 以下关键字后：if, else, for, while, do, switch, case, try, catch, finally, with, return, typeof
- 单行注释'//'后，多行注释'*'后
- 对象的属性值前
- for循环，如示例
- 声明函数或函数表达式'{'前
- 函数的参数之间  

如：
``` javascript
var a = {
    b: 1
}

++x;
y++;
z = x ? 1 : 2;

var a = [1, 2];
var a = (1 + 2) * 3;

for (int i = 0; i < 8; i++) {
    i++;
}
```

### **空行**
需要空行的几种情况：
- 变量声明后
- 注释前 
- 代码块后
- 文件最后保留一个空行  

如：
``` javascript
var a, 
    foo = 7,
    b, c, d = 8;
``` 

### **注释**
1. 单行注释
    - 双斜线后 + 一个空格；
    - 缩进与下一行代码保持一致
    - 可位于代码行的末尾，与代码间隔一个空格  

    如：
    ``` javascript
    if (condition) {
        // if you make something, check the password
        allowed();
    }

    var onething = 'onething'; // one space after code
    ``` 

2. 多行注释  

    最少三行， '*'后面 + 一个空格，建议使用情况如下：
    - 难于理解的代码段
    - 可能存在错误的代码段
    - 浏览器特殊的hack代码
    - 业务逻辑强相关的代码  

    如：
    ``` javascript
    /*
    * one space after '*'
    */
    var x = 1;
    ```
3. 文档注释  

    建议使用情况
    - 所有常量
    - 所有函数
    - 所有类  

    如：
    ``` javascript
    /**
    * @func
    * @ param {string} a - 参数a
    * @ param {number} b=1 - 参数b默认值为1
    * @ param {object} c - 参数c是一个对象
    * @ param {object[]} d - 参数d是一个对象数组
    * @ param {string} e.h - 参数e的h属性
    * @ param {string} [f] - 参数f是一个可选参数
    */
    function foo(a, b, c, d, e, f) {
        ... 
    }
    ```

### **变量命名**
- 标准变量采用驼峰命名法
- 'ID'在变量名中全大写
- 'URL'在变量名中全大写
- 'Android'在变量名中大写第一个字母
- 'iOS'在变量名中小写第一个，大写后两个字母
- 常量全大写，用下划线连接
- 构造函数，大写第一个字母
- jquery对象必须以'$'开头命名  

如：
``` javascript
var thisIsMyName;

var goodID;

var reportURL;

var AndroidVersion;

var iOSVersion;

var MAX_COUNT = 10;

function Person(name) {
    this.name = name;
}

var $body = $('body')
```

### **数组、对象**
- 对象属性名不需要加引号
- 对象以缩进的形式书写，不要写在一行
- 数组、对象最后不要有逗号

如：
``` javascript
var a = {b: 1};

var a = {
    b: 1,
    c: 2
}
```

### **括号**
- 以下关键字后必须有大括号：if, else, for, while, do, swith, try, catch, finally, with;

### **null**
适用场景：
- 初始化一个将来可能被赋值的对象的变量
- 与已经初始化的变量进行比较
- 作为一个参数为对象的函数的调用传参
- 作为一个返回对象的函数的返回值  

不适用场景：
- 不要用null来判断函数调用时有无传参
- 不要与未初始化的变量进行比较

### **undefined**
- 永远不要直接使用undefined进行变量判断；
- 使用typeod和字符串'undefined'对变量进行判断

### **jshint**

### **其他**
- 不要混用tab和space
- 不要在一处使用多个tab或space
- 换行符统一用'LF'
- 对上下文this的引用只能使用'_this','that','self'其中一个来命名
- 行尾不要有空白字符
- switch的falling through和no default的情况一定要有注释特殊说明
- 不允许有空的代码块