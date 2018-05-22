---
layout: post
title: 原型继承
description: 
category: blog
---

> 引用 [Javascript继承机制的设计思想](http://www.ruanyifeng.com/blog/2011/06/designing_ideas_of_inheritance_mechanism_in_javascript.html)

## Javascript的继承问题？
先看一下C#是如何创建并实例化一个类的：
``` c#
    class Program
    {
        static void Main(string[] args)
        {
            Dog dog = new Dog("orange", 1);
            Console.Write(string.Format("dog's name is {0}, age is {1}, species is {2}, volice is {3}", 
                dog.name, dog.age, dog.species, dog.volice));
        }
    }

    public class Animal
    {
        public string name;
        public string species = "动物";

        public Animal(string name)
        {
            this.name = name;
        }
    }

    public class Dog : Animal
    {
        public string volice = "wanwan";
        public int age;

        public Dog(string name, int age) : base(name)
        {
            this.name = name;
            this.age = age;
        }
    }
```

接下来我们思考一下Javascript如何实现呢？
首先，Javascript没有类的概念，于是借鉴了其他语言创建实例时都会调用类的构造函数的特点。
``` javascript
    function Dog(name) {
        this.name = name;   //注意：this代表了新创建的实例对象
    }

    var dog1 = new Dog('apple');
```
但是以上做法有一个问题，就是无法共享属性和方法，还会造成极大的资源浪费，怎么办呢？

## prototype属性的引入
prototype包含prototype对象，所有需要共享的属性和方法都放在这个对象里，而那些无需共享的属性和方法则放在构造函数里面。
``` javascript
    function Dog(name) {
        this.name = name;
    }

    Dog.prototype = { species: '动物' };   //这里的species对象是所有实例共享的，修改该对象，会同时影响所有实例

    var dog1 = new Dong('apple');
    console.log(dog1.species);
```
## 总结：由于所有实例共享prototype对象，因此从外界看起来，prototype对象就好像是实例对象的原型，而实例则好像继承了prototype对象一样。
