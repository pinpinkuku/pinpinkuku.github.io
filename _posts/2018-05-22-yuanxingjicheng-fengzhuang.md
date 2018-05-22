---
layout: post
title: 封装继承
description: 
category: blog
---

> 引用 [Javascript 面向对象编程（一）：封装](http://www.ruanyifeng.com/blog/2010/05/object-oriented_javascript_encapsulation.html)     

> 引用 [Javascript面向对象编程（二）：构造函数的继承](http://www.ruanyifeng.com/blog/2010/05/object-oriented_javascript_inheritance.html)     

> 引用 [Javascript面向对象编程（三）：非构造函数的继承](http://www.ruanyifeng.com/blog/2010/05/object-oriented_javascript_inheritance_continued.html)

## 封装
Javascript是一种基于对象的语言，但是又没有class类，如何封装其属性和方法呢？
- 原始模式
``` javascript
    var Cat = {
        name: '',
        age: ''
    }

    var cat1 = {};
    cat1.name = "apple";
    cat1.age = 1;

    var cat2 = {};
    cat2.name = "orange";
    cat2.age = 2;
```
缺点：如果需要多个实例，写起来很麻烦，且实例与原型之间看不出有任何联系。

- 原始模式改进
``` javascript
    function Cat(name, age) {
        return {
            name: name,
            age: age
        }
    }

    var cat1 = Cat("apple", 1);
    var cat2 = Cat("orange", 2);
```
缺点：无法反应出多个实例之间的关系

- 构造函数模式    

    所谓构造函数，其实就是内部使用了this的普通函数。对构造函数使用new运算符，就能生成实例，并且this变量会绑定在实例对象上。
``` javascript
    function Cat(name, age) {
        this.name = name;
        this.age = age;
    }

    // cat1 和 cat2 都有 constructor属性，指向构造函数
    var cat1 = Cat("apple", 1);
    var cat2 = Cat("orange", 2);

    alert(cat1.constructor == Cat);  //true
    alert(cat2.constructor == Cat);  //true

    //instanceof运算符验证原型对象与实例对象之间的关系
    alert(cat1 instanceof Cat);   //true
    alert(cat2 instanceof Cat);   //true
```
缺点：没生成一个实例，属性和方法就拷贝一次，重复的内容不但多占内存，也缺乏效率。

- Prototype模式    

    Javascript规定：每个构造函数都有prototype属性，执行另一个对象。这个对象所有的属性和方法，都被构造函数的实例继承。
``` javascript
    function Cat(name, age) {
        this.name = name;
        this.age = age;
    }

    //所有的属性和方法，其实都是同一个内存地址，指向prototype对象
    Cat.prototype.type = "猫";
    Cat.prototype.eat = function(){
        alert("吃老鼠")
    };

    var cat1 = Cat("apple", 1);
    var cat2 = Cat("orange", 2); 

    alert(cat1.type);
    cat1.eat();

    alert(cat1.eat == cat2.eat);   //true
```
为了配置prototype属性，Javascript还定义了部分辅助方法：
- isPrototypeOf()
- hasOwnProperty()
- in

## 构造函数的继承     

``` javascript
    function Animal() {
        this.species = '动物';
    }

    function Cat(name, age) {
        this.name = name;
        this.age = age;
    }
```
怎么才能使猫对象继承动物对象呢？

- 构造函数绑定
- Prototype模式
- 直接继承Prototype模式
- 利用空对象作为中介
``` javascript
    function extend(Child, Parent) {
        var F = function(){};
        F.prototype = Parent.prototype;
        Child.prototype = new F();

        Child.prototype.constructor = Child;
        //uber属性指向父对象的prototype属性，这等于子对象可以直接调用父对象的方法。
        Child.uber = Parent.prototype;  
    }

    extend(Dog, Animal);
    var dog1 = new new Dog("orange", 1);
    alert(dog1.species);
```
- 拷贝继承
``` javascript
    function Animal() {
        Animal.prototype.species = "动物";
    }

    function extend2(Child, Parent) {
        var p = Parent.prototype;
        var c = Child.prototype;

        for (var i in p) {
            c[i] = p[i];
        }

        c.uber = p;
    }

    extend2(Cat, Animal);

    var cat1 = new Cat("balana1", 1);
    alert(cat1.species);
```

## 非构造函数的继承     

``` javascript
    var Chinese = {
        nation: '中国'
    }

    var Doctor = {
        career: '医生'
    }
```
由于Chinese和Doctor都是普通对象，不是构造函数，无法使用构造函数逇方法实现继承。

- object()方法
``` javascript
    function object(o) {
        function F(){}

        F.prototype = o;
        return new F();
    }

    var Doctor = object(Chinese);
    Doctor.career = '';
```
- 浅拷贝
``` javascript
    function extendCopy(p) {
        var c = {};

        for (var i in p) {
            c[i] = p[i];
        }

        c.uber = p;

        return c;
    }

    var Doctor = extendCopy(Chinese);
    Doctor.career = '';

    //会导致在子属性改变时修改父属性值
```
- 深拷贝
``` javascript
    function deepCopy(p, c) {
        var c = c || {};

        for(var i in p) {
            if (typeof p[i] === 'object') {
                c[i] = (p[i].constructor === Array) ? [] : {};
                deepCopy(p[i] , c[i]);
            } else {
                c[i] = p[i];
            }
        }

        return c;
    }

    var Doctor = deepCopy(Chinese);
```

## 附录：一道面试题     
写一个 subMath 继承 Math，并重写 random 方法返回 0 ~ 9 的数字    

``` javascript
    function subMath(){}

    function extend(Child, Parent) {
        var F = function(){};
        F.prototype = Parent.prototype;
        Child.prototype = new F();
    }

    extend(subMath, Math);

    subMath.prototype.random = function() {
        return Math.random() * 10;
    }
```
