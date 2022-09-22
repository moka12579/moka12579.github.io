---
title: 初识React
date: 2022-09-22 11:55:48
tags: react
categories: 	
 - resct基础
---

# 初识React



## 预备知识

需要掌握{% link JavaScript https://developer.mozilla.org/zh-CN/docs/Web/JavaScript %}

### 需要掌握的JavaScript基础知识

​	判断 {% link this https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/this %} 的指向

​	{% link class https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/class %} (类)

​	es6语法规范

​	npm包管理器

​	原型、{% link 原型链 https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Inheritance_and_the_prototype_chain %}

​	{% post_link Array对象的方法 数组常用方法 %}

​	模块化



# 认识React

​	React是将数据渲染为HTML视图的开源JavaScript库

​	以往写html网页需要三步：

​		1. 发送请求获取数据

​		2. 处理数据（过滤，格式整理等）

​		3. 操作dom，将数据呈现到页面上

### 	开发人员与时间点

​		由Facebook的软件工程师 Jordan Walke 开发，并且并且开源

​		于2011年部署于 Facebook 的 newsfeed (就是一个页面，类似于微博首屏推荐页面)

​		然后在2012年部署在自家的 Instagram (一个照片分享平台)

​		2013年5月，Facebook宣布 正式开源

##### 		近十年“陈酿” React正在被腾讯、阿里等一线大厂广泛使用



# 为什么要学？

之前操作DOM的痛点：

1. 原生JavaScript操作DOM繁琐效率低 `DOM-API操作UI`

   1. 繁琐：

      1. ` document.getElementById` 一个网页源代码满屏的document

   2. 效率低

      1. 页面上有个id为app的盒子，使用js改变背景颜色就是`document.getElementById("app").style.background="blue"`

      2. 需要三秒钟后再改那就是写一个定时器，延迟三秒钟，三秒钟后再怎么怎么样改样式……

         

2. 使用JavaScript直接操作DOM，浏览器会进行大量 `重绘重排`

3. 原生JavaScript没有 `组件化` 的编码方案，代码复用率低

   1. 组件化：
      1. 一拆到低，js、html结构和css样式都拆
      2. 甚至构成这个局部功能的图片、字体、音视频都要拆
   2. JavaScript模块化：
      1. 将庞大的js，按照功能拆分成小的js
      2. 模块化只是拆了js，html结构和c s s样式没有拆

React的特点：

1. 采用 `组件化` 模式、`声明式编码`，提高开发效率及组件复用率

   1. 声明式编码：

      之前都叫命令式编码

      比如页面上有个红色的盒子，要变成蓝色的

      之前：

      ​		通过js或者jquery拿到红色的盒子，再用 .style 去改变颜色，少一步都不行

      ##### 		这叫命令式编码

      现在：

      ​		通过特殊的语法，只是表达一下是蓝色的，react就把这个红色的盒子变成蓝色

      ##### 	    这叫声明式编码

      ##### 		虽爽，但是需要学习

   2. 在React Native中可以使用React语法进行移动端开发

      1. React Native专门让前端人员用js编写出 Android 和 iOS 应用

   3. 使用 `虚拟DOM` + 优秀的 `Diffing算法` ，尽量减少与真实DOM的交互

      1. 虚拟DOM：
         1. 不会存在于页面上，存在于电脑的内存中，给React用的
      2. Diffing算法

# 几张图解释

用原生js实现显示数据

![截屏2022-09-22 19.42.51](js.png)

如果数组不会更新，静态的页面，写死就可以，如果多了一个人，又要拿一堆数据便利，然后又来了一次innerHTML。但是原来页面中的鹿晗-18，李现-19就不会被复用，被新的innerHTML所覆盖。如下图所示

![截屏2022-09-22 19.46.49](js1.png)

纯js实现：如果原来有100个人，新增了一个人，那么代价就是原来的100个人没一个用得上的，用101个人去重绘了一遍网页

react如何做的

![截屏2022-09-22 19.49.17](react1.png)

React是这么做的

​	数据还是那两个人，React并没有直接动真实DOM，而是创建成了虚拟DOM，然后将虚拟DOM映射成真实DOM

​	优势不是在第一次体现出来的，而是在后期数据更新

​	这时候数据变化，多了一个人，react还是把三条数据都生成虚拟DOM，React并没有把刚才的虚拟DOM丢弃，而是存起来，然后进行虚拟DOM的比较，当之前两个 `虚拟DOM` 比较后没有变化，直接就用起来，其实创建的虚拟DOM也就只是新增的那个1
