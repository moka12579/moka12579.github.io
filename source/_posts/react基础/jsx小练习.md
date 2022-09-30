---
title: jsx小练习
date: 2022-09-26 18:51:10
tags: react基础
categories:	
  - react基础
---

# jsx小练习

需求如下，做这样的一个页面

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/jsx.png)

## 小试一下

```jsx
//上面省略HTML部分
//创建虚拟DON
const VDOM = (
	<div>
  	<h1>前段js框架列表</h1>
    <ul>
    	<li>Angular</li>
      <li>React</li>
      <li>Vue</li>
    </ul>
  </div>
)

//渲染虚拟DOM到页面
ReactDOM.render(VDOM,document.getElementById("test"))
```

效果

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/jsx.png)

真实中肯定不是写死的，下面模拟一些数据

```jsx
//上面省略HTML部分
//模拟一些数据
const data=["Angular","React","Vue"]
//创建虚拟DON
const VDOM = (
	<div>
  	<h1>前段js框架列表</h1>
    <ul>
      // 这样会遍历但是丢失ul和li的结构
      // {data}
    	{
        
        // 只能写js的表达式
        // if判断、for循环都不能写，因为是语句
        data.map((item,index) => {
          return <li key={index}>{item}</li>
        })
      }
    </ul>
  </div>
)

//渲染虚拟DOM到页面
ReactDOM.render(VDOM,document.getElementById("test"))
```

虽然有效果，但是控制台报错如下

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/error.png)

大概意思是 `每一个节点在这个列表中都必须有一个唯一的key属性`

非常优秀的 `Diffing算法` 就依赖这个key，所以每一个人都要有一个标识，key就是标签的唯一标识

如果key给的值一样，则报如下错误

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/error2.png)

大概意思： `说有两个孩子的key一样，而key应该是唯一的`

所以如下所示

```jsx
data.map((item,index) => {
	return <li key={index}>{item}</li>
})
```

但是这样写会有问题，现在就怎么简单怎么来

### 注意区分 `js语句（代码）` 与 `js表达式` 的区别

拿个变量在左侧接，能接到的就是表达式

  1. 表达式：一个表达式会产生一个值，可以存放在任何一个需要值的地方。下面这些都是表达式：
	1. a （变量名）
	2. a+b
	3. demo(1) // demo函数没写返回值也会有默认的返回值为undefind
	4. arr.map() 
	5. function test() {} // 定义函数也有一个返回值

2. 语句（代码） 下面这些都是
   1. if(){}
   2. for(){}
   3. switch(){case:xxx}
