---
title: findLastIndex
date: 2022-09-20 18:53:17
tags: Array.prototype.findLastIndex
---

# Array.prototype.findLastIndex

findLastIndex() 方法和`findIndex`类似，不同的是该方法是从后往前找，`findIndex`从前往后找

#### 注意：虽然此方法从后往前找，但下标仍然是从前往后数

例如

```javascript
let arr = [1,2,5,9,13,5,2]

arr.findLastIndex(v => v>10)
// 返回4而不是返回2
```

### 语法

```javascript
// 箭头函数
findLastIndex((element) => { /* … */ } )
findLastIndex((element, index) => { /* … */ } )
findLastIndex((element, index, array) => { /* … */ } )

// 内联回调函数
findLastIndex(function(element) { /* … */ })
findLastIndex(function(element, index) { /* … */ })
findLastIndex(function(element, index, array){ /* … */ })
findLastIndex(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	提供的测试函数，接收三个参数

​	`element`

​		当前元素

​	`index`

​		当前元素的下标

​	`array`

​		调用当前方法的数组

#### 注意：此方法需要返回一个真值表示当前元素是否通过测试

`thisArg`	`可选`

​	方法的this指向

### 返回值

`number`

​	返回从后往前数第一个通过测试函数的索引值，没有则返回-1

### 示例

找出下列数组中作为素数的最后一个元素的索引，没有则返回-1

```javascript
let arr = [4, 6, 8, 12]

arr.findLastIndex(function(v){
   if (v % 2 === 0 || v < 2) {
    return false;
  }
  for (let factor = 3; factor <= Math.sqrt(v); factor += 2) {
    if (v % factor === 0) {
      return false;
    }
  }
  return true;
})// 返回 -1

let arr1 = [4, 5, 7, 8, 9, 11, 12]
arr1.findLastIndex(function(v){
   if (v % 2 === 0 || v < 2) {
    return false;
  }
  for (let factor = 3; factor <= Math.sqrt(v); factor += 2) {
    if (v % factor === 0) {
      return false;
    }
  }
  return true;
}) // 返回5
```

