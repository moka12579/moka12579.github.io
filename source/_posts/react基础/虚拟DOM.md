---
title: 虚拟DOM
date: 2022-09-24 15:42:08
tags: react
categories: 	
 - react基础
---

# 虚拟DOM

## 两种创建方式

别的都一样，但第二种方式无需引入babel

### 使用JSX

```jsx
		//1. 创建虚拟DOM
  	const VDOM = <h1 id="title">Hello React</h1> // 此处一定不要写引号，因为不是字符串
  	//2. 渲染虚拟DOM到页面
  	// ReactDOM.render(虚拟DOM,容器)
  	// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
  	// 注意这句话不是追加的动作哦，这是替换的动作
  	ReactDom.render(VDOM,document.getElementById("test"))
```



### 使用js

```js
		//1. 创建虚拟DOM
		//document.createElement是创建真实DOM
		//React.createElement是创建虚拟DOM

  	const VDOM = React.createElement('h1',{id:'title'},"Hello,React")
    
  	//2. 渲染虚拟DOM到页面
  	// ReactDOM.render(虚拟DOM,容器)
  	// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
  	// 注意这句话不是追加的动作哦，这是替换的动作
  	ReactDom.render(VDOM,document.getElementById("test"))
```



有个需求，h1标签里有个span标签，span标签里有 `Hello,React`

使用JSX

```jsx
const VDOM = <h1 id="title"><span>Hello,React</span></h1> 
```

使用js

```js
const VDOM = React.createElement('h1',{id:'title'},React.createElement('span',{},"Hello,React"))
```



​		如果有四层HTML嵌套，原生js写就很痛苦，`jsx` 就会很方便，写虚拟DOM就跟当年写HTML一样，`jsx` 就为了解决原生js创建虚拟DOM繁琐的问题，就是为了简单方便的创建虚拟DOM，写起来更加流畅

jsx也支持这样写:

```jsx
const VDOM = (
  <h1 id="title">
    <span>Hello,React</span>
  </h1> 
)
//经过babel的翻译就是
const VDOM = React.createElement('h1',{id:'title'},React.createElement('span',{},"Hello,React"))
```

`jsx` 创建虚拟DOM的写法其实就是原生js创建虚拟DOM的语法糖
