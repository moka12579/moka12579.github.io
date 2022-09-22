---
title: push
date: 2022-09-20 18:53:59
tags: array
categories:
  - Array对象的方法
---

# Array.prototype.push

Push()方法用于在数组后面追加 `最少一个` 元素，返回该数组的新长度

#### 该方法会改变原数组

### 语法

```
push(element0)
push(element0, element1)
push(element0, element1, /* … ,*/ elementN)
```

### 参数

`element`

​	用于添加到数组的元素

### 返回值

`number`

​	返回该数组被追加后的新长度

### 示例

在下面的数组里追加元素

```js
let sports = ["soccer", "baseball"];
let total = sports.push("football", "swimming");

console.log(sports);
// ["soccer", "baseball", "football", "swimming"]

console.log(total);
// 4
```

合并两个数组

```js
let sports = ["soccer", "baseball"];
let sports1 = ["football", "swimming"]

//这里使用了es6的解构
let total = sports.push(...sports1);

console.log(sports);
// ["soccer", "baseball", "football", "swimming"]

console.log(total);
// 4
```

