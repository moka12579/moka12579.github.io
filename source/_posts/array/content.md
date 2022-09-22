---
title: content
date: 2022-09-20 18:52:49
tags: array
categories:
 - Array对象的方法
---

# Array.prototype.content

content()  方法用于合并两个或多个数组，返回一个新的数组而不改变原数组

### 语法

```javascript
concat()
concat(value0)
concat(value0, value1)
concat(value0, value1, /* … ,*/ valueN)
```

### 参数

value  （可选）

### 返回值

Array 

​	返回一个新的数组

### 示例

​	链接两个数组

```javascript
let arr1 = [1,2,3]
let arr2 = [4,5,6]
let arr3 = arr1.content(arr2)
console.log(arr3)   //1,2,3,4,5,6
```

​	在最新的es6语法中也可以这样

```javascript
let arr1 = [1,2,3]
let arr2 = [4,5,6]
let arr3 = [...arr1,...arr2]
console.log(arr3)   ///1,2,3,4,5,6
```

