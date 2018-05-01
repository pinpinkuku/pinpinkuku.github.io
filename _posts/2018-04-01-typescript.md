---
layout: post
title: TypeScript
description: ES6
category: blog
---

### ES5、ES6、JavaScript和TypeScript的关系？
ES是标准，ES5、ES6是两个不同的版本；  
JavaScript、TypeScript是两种语言，分别实现了ES5、ES6标准

### 编译器
大多数浏览器还不支持ES6，因此使用ES6规范编写的代码无法再浏览器中运行，故出现了各类编译器，将ES6翻译成ES5在网页中运行；

### TypeScript常见语法
#### 字符串
- 多行字符串：JS处理多行字符串使用 + 连字符，而TS使用 `` 直接书写，书写简单且易于理解；
- 字符串模板：多行字符串中嵌入变量及方法，如   

``` typescript 
var a = 'world';
var b = `hello ${ a }`;
var func1 = function(){
    return 'world';
}
var d = `hello ${ func1 }`;
```

- 自行拆分字符串       

``` typescript
function test(template, name, age) {
    var myname = "name1";
    var getAge = function() {
        return 18;
    }
}

test`hello my name is ${ myname }, i'm ${ getAge }`
```

### 参数特性
- 定义参数类型：string、boolean、number、any 或对于函数而言的 void，如        

``` typescript
var myname: string = "soho";

var alias = "sofa";
    alias = 13;  tips: error 

function test:void (a: string, b?: string, c: string = 'somany') {
    
}
```

- 定义参数默认值  
注意：带有默认值的参数顺序必须在不带默认值参数的后面   

``` typescript
function test:void (a: string, b: string, c: string = 'somany') {
    
}
```

- 定义可选参数   

``` typescript
function test:void (a: string, b?: string, c: string = 'somany') {
    
}
```

### 函数特性
- Rest和Spread   
... 表示任意个参数   

``` typescript
function fun1(...args) {

}
```

- Generator   
暂停、恢复代码执行

``` typescript
function* dosomething(){
    console.log("i am start");
    yield;
    console.log("i am end");
}

var func1 = dosomething();
func1.next();
func1.next();
```

### 析构表达式
- 对象    

``` typescript
function getsomething(){
    return {
        code: "dell",
        price: 100
    }
}

var t = getsomething();p
var code = t.code;
var price = t.price;

var {code, price} = getsomething();
var {code: codex, price} = getsomething();
console.log(codex);
``` 
- 数组    

``` typescript
var array = [1, 2, 3, 4];
var [number1, number2] = array;
var [, , number1, number2] = array;
``` 

### 表达式和循环
- 箭头表达式：声明匿名函数
- 循环     

``` typescript
var myArray = [1, 2, 3, 4];
myArray.desc = "there is a error";

// 忽略属性，不能break
myArray.forEach(value => console.log(value));

// 元素 + 属性的循环
for (var n in myArray) {
    console.log(n);
    // 0 1 2 3 desc
}
for (var n in myArray) {
    console.log(myArray[n]);
    // 1 2 3 4 there is a error
}

// 忽略属性值 可以break
for (var n of myArray) {
    if (n > 2) break;
    console.log(n);
    // 1 2
}
```

### 面向对象
- 访问控制符  
public： 默认  
private：仅类内部   
protected： 类及其子类内部
- 类的构造函数

### 泛型
``` typescript
var workers: Array<Person> = [];
workers[0] = new Person("");

```

