---
title: find
date: 2022-09-20 18:53:08
tags: Array.prototype.find
---

# Array.prototype.find

find() 返回方法列表中满足测试函数的第一个元素的值，没有则返回`undefind`

- 如果要找到元素的索引，请使用{% post_link findIndex Array.prototype.findIndex %}

### 语法

```javascript
// 箭头函数
find((element) => { /* … */ } )
find((element, index) => { /* … */ } )
find((element, index, array) => { /* … */ } )

// 回调函数
find(callbackFn)
find(callbackFn, thisArg)

// 内联回调函数
find(function(element) { /* … */ })
find(function(element, index) { /* … */ })
find(function(element, index, array){ /* … */ })
find(function(element, index, array) { /* … */ }, thisArg)
```
