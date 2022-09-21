---
title: map
date: 2022-09-20 18:53:53
tags: Array.prototype.map
---

# Array.prototype.map

map()方法返回一个新数组，新数组由原数组中元素通过提供的函数组成

### 语法

```
// 箭头函数
map((element) => { /* … */ })
map((element, index) => { /* … */ })
map((element, index, array) => { /* … */ })

// 内联回调函数
map(function(element) { /* … */ })
map(function(element, index) { /* … */ })
map(function(element, index, array){ /* … */ })
map(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	提供的测试函数，接收三个值

​	`	element`

​		数组里的元素

​	`index`

​		当前元素的下标

​	`array`

​		调用map方法的数组

`thisArg`	`可选`

​	该测试函数使用的this对象

### 返回值

`array`

​	一个新数组，使用通过提供的函数的元素组成

### 示例

求下列数组的平方根并放入新数组

```js
let number = [1,4,9]
number.map(v => Math.sqrt(v)) // [1,2,3]
// number依旧是[1,4,9]
```

将下列数组中的数字乘以2

```js
let number = [1,4,9]
number.map(v => v*2) //[2,8,18]
// number依旧是[1,4,9]
```



