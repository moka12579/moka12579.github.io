---
title: forEach
date: 2022-09-20 18:53:24
tags: Array.portotype.forEach
categories:
 - js基础
  - Array对象的方法
---

# Array.portotype.forEach

forEach()方法用于循环数组，类似for(let i=0;i<arr.lenth;i++){}，不同的是`forEach只能用于循环数组，fori还可以循环字符串`

#### 注意：

- forEach是表达式，而fori是语句

 - forEach只能用抛出错误打断，无法使用`break`打断。如有退出循环的需要可使用
   - fori
   - for ... of
   - for ... in

​	

### 语法

```js
// 箭头函数
forEach((element) => { /* … */ })
forEach((element, index) => { /* … */ })
forEach((element, index, array) => { /* … */ })

// 内联回调函数
forEach(function(element) { /* … */ })
forEach(function(element, index) { /* … */ })
forEach(function(element, index, array){ /* … */ })
forEach(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	为数组中每个元素执行的函数。

​	函数调用时带有以下参数：

​	`element`

​		数组中正在处理的当前元素。

​	`index`

​		数组中正在处理的当前元素的索引。

​	`	array`	

​		`forEach()` 方法正在操作的数组。

`thisArg` 	`可选`

​	执行函数时所使用的this

### 示例

不对未初始化的值进行任何操作，连输出都不会

```js
let arr = [1,2,3,/* empty */,7]


arr.forEach(function(v) {
  console.log(v)
})
//输出1，2，3，7
//中间的空值不会被输出
```

