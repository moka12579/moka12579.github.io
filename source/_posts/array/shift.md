---
title: shift
date: 2022-09-20 18:54:11
tags: array
categories:
  - Array对象的方法
---

# Array.prototype.shift

shift()方法用于在数组的最前面删除元素，并返回被删除的元素

#### 会更改原数组

### 语法

```js
shift()
```

### 返回值

返回被删除的元素，数组为空则返回 `undefind`

### 示例

删除以下数组中第一个元素

```js
let arr = [1,2,3]

console.log(arr) //[1,2,3]

arr.shift()

console.log(arr) //[2,3]
```

