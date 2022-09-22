---
title: some
date: 2022-09-20 18:54:20
tags: array
categories:
  - js基础
  - Array对象的方法
---

# Array.prototype.some

some()方法测试数组中是不是至少有一个元素通过了提供的测试函数。

是就返回true，不是则返回false

### 语法

```js
// 箭头函数
some((element) => { /* … */ } )
some((element, index) => { /* … */ } )
some((element, index, array) => { /* … */ } )

// 内联回调函数
some(function(element) { /* … */ })
some(function(element, index) { /* … */ })
some(function(element, index, array){ /* … */ })
some(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	用来测试每个元素的函数，接受三个参数：

​		`element`

​			数组中正在处理的元素。

​		`index`	`可选`

​			数组中正在处理的元素的索引值。

​		`array`	`可选`

​			`some()`被调用的数组。

`thisArg`	`可选`

执行 `callback` 时使用的 `this` 值。

### 返回值

`boolean`

​	返回一个布尔值，代表是否至少有一个元素通过了提供的测试函数

### 示例

检测下面数组中是否有元素大于10

```js
let arr1 = [9,1,19,3,2,6]
let arr2 = [7,1,5,9,1]

arr1.some(function(v){
  return v>10
})// true

arr1.some(function(v){
  return v>10
})// false

//使用es6的箭头函数

arr1.some(v => v>10)// true

arr1.some(v => v>10) // false
```

