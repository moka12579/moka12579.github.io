---
title: findIndex
date: 2022-09-20 18:53:10
tags: Array.prototype.findIndex
---

# Array.prototype.findIndex

findIndex()方法返回当前数组中满足提供的测试函数的第一个元素的索引，若都不满足则返回-1

- 若要找到元素，请使用{% post_link find Array.prototype.find %}

### 语法

```javascript
// 箭头函数
findIndex((element) => { /* … */ } )
findIndex((element, index) => { /* … */ } )
findIndex((element, index, array) => { /* … */ } )

// 内联回调函数
findIndex(function(element) { /* … */ })
findIndex(function(element, index) { /* … */ })
findIndex(function(element, index, array){ /* … */ })
findIndex(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	提供测试的函数，可以接收三个参数

​	`element`

​		当前元素

​	`index`

​		当前元素的下标

​	`array`

​		调用该方法的数组

`thisArg`	`可选`

​	该方法所使用的this

### 返回值

`number`

​	返回第一个元素通过测试函数的下标，都不通过返回-1

### 示例

查找数组中第一个质数的索引

```javascript
let arr = [4, 6, 8, 12]

arr.findIndex(function(v){
  var start = 2;
  while (start <= Math.sqrt(v)) {
    if (v % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}) //-1 没有质数

let arr1 = [4, 6, 7, 12]

arr1.findIndex(function(v){
  var start = 2;
  while (start <= Math.sqrt(v)) {
    if (v % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}) //2 7是质数
```

