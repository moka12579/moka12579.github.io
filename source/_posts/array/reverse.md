---
title: reverse
date: 2022-09-20 18:54:04
tags: array
categories:
  - Array对象的方法
---

# Array.prototype.reverse

reverse()方法用于颠倒一个数组，并返回该数组。

此数组的最后一项将变为第一项，倒数第二项将变为第二项，以此类推。

#### 注意：reverse()会改变原数组

### 语法

```js
reverse()
```

### 返回值

`array`

​	返回原数组颠倒后的数组

### 示例

颠倒数组中的元素。

reverse()会改变原数组

```js
const a = [1, 2, 3];

console.log(a); // [1, 2, 3]

a.reverse();

console.log(a); // [3, 2, 1]
```

