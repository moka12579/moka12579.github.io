---
title: find
date: 2022-09-20 18:53:08
tags: Array.prototype.find
categories:
 - js基础
  - Array对象的方法
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


// 内联回调函数
find(function(element) { /* … */ })
find(function(element, index) { /* … */ })
find(function(element, index, array){ /* … */ })
find(function(element, index, array) { /* … */ }, thisArg)
```

### 参数

`callback`

​	该数组上每一个元素要执行的函数，该函数接收3个参数

​	`element`

​		该数组的元素

​	`index`

​		当前元素的下标

​	`array`

​		调用当前方法的数组

#### 注意：该函数必须返回一个真值标识找到了匹配的元素

`thisArg`		`可选`

​	调用该方法时使用的this

### 示例

用对象的属性找数组里的对象

```javascript
const inventory = [
  {name: 'apples', quantity: 2},
  {name: 'bananas', quantity: 0},
  {name: 'cherries', quantity: 5}
];

console.log(inventory.find(function(fruit) {
  return fruit.name === 'cherries';
}));
// {name: 'cherries', quantity: 5}
```

使用箭头函数

```javascript
const inventory = [
  {name: 'apples', quantity: 2},
  {name: 'bananas', quantity: 0},
  {name: 'cherries', quantity: 5}
];

console.log(inventory.find(v=>v.name === "bananas"))  
/*等同于 
console.log(inventory.find(v=>{
	retuen v.name === "bananas" 
}))
*/
// {name: 'bananas', quantity: 0}
```

