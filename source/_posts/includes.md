---
title: includes
date: 2022-09-20 18:53:30
tags: Array.prototype.includes
---

# Array.prototype.includes

includes()  方法判断一个数组中是否包含一个指定的值，包含返回`true`，不包含返回`false`

#### 注意：该方法比较字符串和字符时区分大小写

### 语法

```js
includes(searchElement)
includes(searchElement, fromIndex)
```

### 参数

`searchElement`

​	需要查找元素的值

`fromIndex`	`可选`

​	从数组的第几项开始查找

​	如果该值为负数，计算出的索引将作为开始搜索`searchElement`的索引，如果计算的结果小于0，则搜索整个数组

### 返回值

`boolean`

​	返回一个布尔值`boolean`，如果在数组或者`formIndex`指定下标开始查找的范围内找到`searchElement`，则返回`true`，否则返回`false`

### 示例

```js
[1,2,3].includes(1) // true
[1,2,3].includes(4) // false
[1,2,3].includes(3,3) // true
[1,2,3].includes(2,-1) // false
[1,2,3].includes(3,-1) // true
[1,2,NaN].includes(Nan) // true
```

formIndex大于数组长度

```js
[1,2,3].includes(2,4) // false
[1,2,3].includes(2,100) // false
```

formIndex为负数

```js
[1,2,3].includes(2,-2) // true
[1,2,3].includes(1,-2) // false
[1,2,3].includes(2,-100) // true
```

