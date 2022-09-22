---
title: splice
date: 2022-09-20 18:54:31
tags: array
categories:
  - js基础
  - Array对象的方法
---

# Array.prototype.splice

splice()方法可以删除元素，查找替换现有元素或添加新的元素来修改数组。

此方法会改变原数组

### 语法

```js
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, ...)
```

### 参数

`start`

​	指定修改的开始位置（从 0 计数）。

`deleteCount`	`可选`

​	整数，表示要移除的数组元素的个数。

`item1, item2, ...`	`可选`

​	要添加进数组的元素，从`start` 位置开始。如果不指定，则 `splice()` 将只删除数组元素。

### 返回值

由被删除的元素组成的一个数组。如果没有删除元素则返回空数组

### 示例

从索引 2 的位置开始删除 0 个元素，插入“drum”

```js
var myFish = ["angel", "clown", "mandarin", "sturgeon"];
var removed = myFish.splice(2, 0, "drum");

// 运算后的 myFish: ["angel", "clown", "drum", "mandarin", "sturgeon"]
// 被删除的元素: [], 没有元素被删除
```

从索引 2 的位置开始删除 0 个元素，插入“drum” 和 "guitar"

```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum', 'guitar');

// 运算后的 myFish: ["angel", "clown", "drum", "guitar", "mandarin", "sturgeon"]
// 被删除的元素: [], 没有元素被删除
```

从索引 3 的位置开始删除 1 个元素

```js
var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
var removed = myFish.splice(3, 1);

// 运算后的 myFish: ["angel", "clown", "drum", "sturgeon"]
// 被删除的元素: ["mandarin"]
```
