---
title: every
date: 2022-09-20 18:52:55
tags: Array.prototype.every
categories:
 - js基础
  - Array对象的方法
---

# Array.prototype.every

every()  方法测试一个数组内的所有元素是否都能通过某个指定的函数测试。返回的是布尔值

此方法不会改变原数组

### 注意：若收到一个空数组，则任何情况下都会返回 ```true```

### 语法

```javascript
//箭头函数
every((element) => { /* … */ })
every((element, index) => { /* … */ })
every((element, index, array) => { /* … */ })

// 内联回调函数
every(function(element) { /* … */ })
every(function(element, index) { /* … */ })
every(function(element, index, array){ /* … */ })
every(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

```callback```

用来测试每个元素的函数，同时可以接受三个参数：

​	```element```

​		用来测试的当前值

​	```index```

​		用来测试的当前值的索引

​	```array```

​		调用every的当前数组

`thisArg`	`可选`

​	执行 `callback` 时使用的 `this` 值。

### 返回值

如果回调函数的每一次返回都为真值，返回 `true`，否则返回 `false`。

(真值是指除 `false`、`0`、`-0`、`0n`、`""`、`null`、`undefined` 和 `NaN` 以外所有的值)

### 示例

检测数组里所有的元素是否大于10

```javascript
let arr = [5,9,11,18,2,5,14]

arr.every(function (element, index, array){
        return element > 10
    })
// false

//箭头函数 更简洁
arr.every(v => v>10) //false

let arr1 = [15,19,11,18,12,15,14]

arr1.every(function (element, index, array){
        return element > 10
    })
// true

//箭头函数 更简洁
arr1.every(v => v>10) //true

```

