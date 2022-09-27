---
title: js类的基本知识
date: 2022-09-27 17:20:31
tags: 复习
categories:	
  - 复习
---

# js类的基本知识

## 类的基本概念

创建一个Person类

```js
class Person {}
```

创建一个Person的实例对象

```js
const p1 = new Person()

console.log(p1)
// Person{}
```

再创建一个实例对象

```js
const p2 =  new Proson()

console.log(p2)
// Person{}
// p2和p1一模一样
```

每个人都有自己不同的属性，就需要传进去

比如p1叫Tom，年龄18，p1叫jerry，年龄19

```js
const p1 = new Person("Tom",18)
const p2 = new Person("jerry",19)
//传了没有接就是没有
```

构造器方法

```js
class Person {
  //构造器方法
  constructor(name,age){
    //构造器中的this就是类的实例对象
    //谁new的，this就是指向谁
    this.name=name
    this.age=age
  }
}
```

此时再输出就会有

```js
console.log(p1)
console.log(p2)
// Person{"Tom",18}
// Person{"jerry",19}
// 每个人就有了自己独有的信息
```

一般方法（除了构造器，根据业务要求写的都叫一般方法）

```js
class Person {
  //构造器方法
  constructor(name,age){
    //构造器中的this就是类的实例对象
    //谁new的，this就是指向谁
    this.name=name
    this.age=age
  }
  // 一般方法
  speak(){
    console.log(`我叫${this.name},我的年龄是${this.age}`)
  }
}
p1.speak() // 我叫Tom，我的年龄是18
p2.speak() // 我叫jerry，我的年龄是19
```

speak方法放在了哪里 —— 类的原型对象上，供实例使用

通过Person实例调用speak时，speak中的this就是Person实例

## 类的继承

一个Person类

```js
class Person{
  constructor(name,age){
    //构造器中的this就是类的实例对象
    //谁new的，this就是指向谁
    this.name=name
    this.age=age
  }
}
```

创建一个student类，继承于Person类

```js
class Student extends Person{}
```

此时student类就有了Person类的方法

建一个学生的实例

```js
const s1 = new Student("小张",15)

console.log(s1) // Student{"小张",15}
```

对于学生这个类而言，构造器可以不用谢

学生有一个年级的属性

```js
const s1 = new Student("小张",15,"高一")
//因为学生类没有年级这个属性，自然高一也就接收不到
```

学生类里就需要写构造器

```js
class Student extends Person{
  constructor(name,age,grade){
    this.name=name
    this.age=age
    this.grade=grade
  }
}
```

此时会报错 `Must call super` super必须调用

当类满足 `定义一个类` `继承一个类` `有自己的构造器` 这三个条件时就必须调用super，不调用就报错，这是类的语法

不写构造器就可以不写super

super：帮你调用父类的构造器

构造器可以替换成如下

```js
class Student extends Person{
  constructor(name,age,grade){
    super(name,age) //注意：super必须在最开始调用
    this.grade=grade
  }
}
```

此时再输出就有了

```js
const s1 = new Student("小张",15,"高一")
// Studet{"小张",15,"高一"}
```

s1可以通过原型链调用到speak，但是此时学生要求说出姓名年龄和年级

```js
class Student extends Person{
  constructor(name,age,grade){
    super(name,age) //注意：super必须在最开始调用
    this.grade=grade
  }
  //重写从父类继承的方法
  speak(){
    console.log(`我叫${this.name},我的年龄是${this.age},我读的是${this.grade}年级`)
  }
}

s1.speak() // 我叫小张，我的年龄是15，我读的是高一年级

```

学生想要有个独有的学习方法

```js
class Student extends Person{
  constructor(name,age,grade){
    super(name,age) //注意：super必须在最开始调用
    this.grade=grade
  }
  //重写从父类继承的方法
  speak(){
    console.log(`我叫${this.name},我的年龄是${this.age},我读的是${this.grade}年级`)
  }
  study(){
    console.log("我很努力的学习")
  }
}

//s1就可以调用学习方法
s1.study() // 我很努力的学习
```

## 总结

1. 类中的构造器不是必须写的，要对实例进行一些初始化操作，如添加指定属性时才写
1. 如果A类继承了B类，且A类中写了构造器，那么A类构造器中super是必须要调用的
1. 类中定义的方法，都是放在了累的原型对象上，供实例去使用
