---
title: slice
date: 2022-09-20 18:54:17
tags: array
categories:
  - js基础
  - Array对象的方法
---

# Array.prototype.slice

Slice()方法返回一个新数组，新数组为方法里的 `start` 和 `end` 截取的元素组成。

#### 此方法不会改变原数组，并且截取的范围包括 `start` ，不包括 `end` 

### 语法

```js
slice()
slice(start)
slice(start,end)
```

### 参数

`start`	`可选`

​	从数组的第几位开始

`end`	`可选`

​	到数组的第几位结束（不包括该项对应的元素）

### 返回值

`array`

​	截取后的数组

### 示例

返回已有数组中的部分元素

```js
let fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];

console.log(fruits.slice(1, 3)) 
// 因为不会包含第二个参数所对应的元素
// ['Orange', 'Lemon']

console.log(fruits.slice(1)) 
// 返回从下标1开始所有的元素
// ['Orange', 'Lemon', 'Apple', 'Mango']
```

