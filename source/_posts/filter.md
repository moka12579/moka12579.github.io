---
title: filter
date: 2022-09-20 18:53:04
tags: Array.prototype.filter
---

# Array.prototype.filter

filter() 方法创建给定数组一部分的`浅拷贝`，其包含通过所提供函数实现的测试的所有元素。

### 语法

```javascript
// 箭头函数
filter((element) => { /* … */ } )
filter((element, index) => { /* … */ } )
filter((element, index, array) => { /* … */ } )

// 内联回调函数
filter(function(element) { /* … */ })
filter(function(element, index) { /* … */ })
filter(function(element, index, array){ /* … */ })
filter(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	回调函数，函数返回true则代表该元素通过函数内的测试，保留该元素；返回false则没通过函数内的测试，舍弃该元素

​	接受以下三个参数：

​	`element`

​		当前元素

​	`index`

​		当前元素的索引值

​	`array`

​		调用filter的数组

`thisArg`	`可选`

​	执行回调函数时使用的this

### 返回值

一个新的数组，由测试的元素组成，如果没有元素通过测试则返回空数组

### 示例

找出符合条件的值

```javascript
let arr = [12, 5, 8, 130, 44]
arr.filter(function(v) {
  return v> 10
})
// [12,130,44]
```

