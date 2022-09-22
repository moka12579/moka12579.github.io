---
title: unshift
date: 2022-09-20 18:54:52
tags: array
categories:
  - Array对象的方法
---

# Array.prototype.unshift

unshift()方法用于将最少一个元素加入到数组的开头

#### 注意：此方法性能不如 {% post_link array/push %} 方法。如无特殊需求，最好使用 {% post_link array/push %}

#### 此方法在将n位元素插入数组的开头时，数组里原来的元素都将被往后移n位

### 语法

``` js
unshift(element0)
unshift(element0, element1, ...)
```

### 参数列表

`elementN`

​	要添加到数组开头的元素。

### 返回值

返回调用方法对象的新 [`length`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/length) 属性值。

### 示例

使用 unshift()

```js
const arr = [1, 2];

arr.unshift(0);               // 调用的结果是3，这是新的数组长度
// arr is [0, 1, 2]

arr.unshift(-2, -1);          // 新的数组长度为5
// arr is [-2, -1, 0, 1, 2]

arr.unshift([-4, -3]);        // 新的数组长度为 6
// arr is [[-4, -3], -2, -1, 0, 1, 2]

arr.unshift([-7, -6], [-5]);  // 新的数组长度为 8
// arr is [ [-7, -6], [-5], [-4, -3], -2, -1, 0, 1, 2 ]
```
