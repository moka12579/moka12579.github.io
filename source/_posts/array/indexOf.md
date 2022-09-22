---
title: indexOf
date: 2022-09-20 18:53:35
tags: array
categories:
  - Array对象的方法
---

# Array.prototype.indexOf

indexOf()方法返回找到指定元素的下标，没有找到就返回-1

#### 注意：

- 该方法使用的全等 `===` 比较

- 该方法不能用于查找对象，如果要查找数组里对象的下标，请使用{% post_link array/findIndex %}

### 语法

``` js
indexOf(searchElement)
indexOf(searchElement, fromIndex)
```

### 参数

`searchElement`

​	要查找的元素

`fromIndex`

​	要从第几个开始查找

### 返回值

`number`

​	提供的值在数组里第一次出现的下标，没有则返回-1

### 示例

```js
let arr = [1,2,3]

arr.indexOf(2)    // 1
arr.indexOf(8)    //-1
arr.indexOf(1,2)  //-1
arr.indexOf(1,-1) //-1
```

当要查找对象时

```js
let arr = [{
  name:"鹿晗",
  age:21
},{
  name:"坤坤",
  age:22
}]

arr.indexOf({
  name:"坤坤",
  age:22
})
//-1
//因为两个对象的内存地址不一样，全等运算就为false
//除非如下所示

let a = {
  name:"坤坤",
  age:22
}

let arr = [{
  name:"鹿晗",
  age:21
},a]

arr.indexOf(a) // 1
//当然这就没什么必要了
```

