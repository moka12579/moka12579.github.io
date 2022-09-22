---
title: sort
date: 2022-09-20 18:54:26
tags: array
categories:
  - Array对象的方法
---

# Array.prototypr.sort

soft()方法会对数组进行排序，并返回该数组

#### 此方法会改变原数组

### 语法

```js
// 无函数
sort()

// 箭头函数
sort((a, b) => { /* … */ } )

// 内联比较函数
sort(function compareFn(a, b) { /* … */ })
```

### 参数

`callback`	`可选`

​	用来指定某种顺序的函数。如果不传该值，会将所有元素转换为 `string` 进行排序，会出现问题。

​	该函数需要返回一个真值代表a和b的区别

​	该函数可接收两个参数：

​	`a`

​		当前元素

​	`b`

​		下一个元素

### 返回值

排序后的数组。会改变原数组

### 示例

对下列数组排序

```js
let arr = [9,3,6,1,4,0,1,5]

arr.sort()

console.log(arr) // [0, 1, 1, 3, 4, 5, 6, 9]

//当arr的数组里存在两位数时
arr = [9,3,6,1,4,0,1,5,11]

arr.sort()

console.log(arr) 
//[0, 1, 1, 11, 3, 4, 5, 6, 9]
//此时就需要自定义排序的方法
//soft()会将全部元素转换成字符串，所以 "1">"11" 就为 false

arr.sort(function(a,b){
  return a-b
})

console.log(arr) // [0, 1, 1, 3, 4, 5, 6, 9, 11]
```

当数组里存在对象时，要求根据年龄的从小到大排序

```js
let arr = [{
    name:"坤坤",
    age:21
  },{
    name:"鹿晗",
    age:19
  },{
    name:"张一山",
    age:32
  }]

//此时sort()方法就必须携带一个函数来自定义排序

arr.sort(function(a,b){
  return a.age-b.age
})

console.log(arr) // [{name: '鹿晗', age: 19}, {name: '坤坤', age: 21}, {name: '张一山', age: 32}]

//es6也可以这样写
arr.sort((a,b) => a.age - b.age)

console.log(arr) // [{name: '鹿晗', age: 19}, {name: '坤坤', age: 21}, {name: '张一山', age: 32}]
```

