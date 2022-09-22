---
title: pop
date: 2022-09-20 18:53:56
tags: array
categories:
  - js基础
  - Array对象的方法
---

# Array.prototype.pop

pop()方法用于删除指定数组中的最后一个元素，此方法会改变原数组



### 语法

```js
pop()
```

### 返回值

从数组中删除的元素，数组为空时返回 `undefind`

### 示例

删掉数组里最后一个元素

```js
const myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];

const popped = myFish.pop();

console.log(myFish); // ['angel', 'clown', 'mandarin']

console.log(popped); // 'sturgeon'
```



