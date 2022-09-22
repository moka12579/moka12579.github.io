---
title: join
date: 2022-09-20 18:53:39
tags: array
categories:
  - Array对象的方法
---

# Array.prototype.join

join()方法将一个数组的元素拼接成字符串

类似：

```js
let arr = [1,2,3]
let str = ""
for(let i=0;i<arr.length;i++){
  i!=arr.length-1?str+=(arr[i]+","):str+=arr[i]
}
//str为1,2,3
```

### 语法

```js
join()
join(separator)
```

### 参数

`separator`	`可选`

​	使用指定的分隔符拼接数组里的元素

​	不传该值则默认为 `,`

​	如果传的是字符串 `"" `，则元素之间没有任何字符

### 返回值

`string`

​	返回拼接后的字符串

### 示例

使用4种不同的分隔符拼接数组

```js
let arr = ['Wind', 'Rain', 'Fire'];

arr.join()  // Wind,Rain,Fire

arr.join("-") //Wind-Rain-Fire

arr.join("+") //Wind+Rain+Fire

arr.join(" ") //Wind Rain Fire
```

