---
title: 虚拟DOM与真实DOM
date: 2022-09-24 15:58:23
tags: react
categories: 	
 - react基础
---

# 虚拟DOM与真实DOM

## 虚拟DOM

输出一下虚拟DOM

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>hello_react</title>
</head>
<body>
<!-- 准备"容器" -->
<div id="test"></div>
  <div id='demo'></div>
  <!-- 引入js -->
  <!-- 引入react核心库 -->
  <script src="../js/react.development.js"></script> <!--全局多了一个对象 React -->
  <!-- 引入react-dom，用于支持react操作DOM -->
	<script src="../js/react-dom.development.js"></script><!--全局多了一个对象 ReactDOM -->
  <!-- 引入babel，用于将jsx转为js -->
	<script src="../js/babel.min.js"></script>
  <script type="text/babel"> // 此处一定要写babel，不写就是js
  	//1. 创建虚拟DOM
  	const VDOM = <h1>Hello React</h1> // 此处一定不要写引号，因为不是字符串
  	//2. 渲染虚拟DOM到页面
  	// ReactDOM.render(虚拟DOM,容器)
  	// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
  	// 注意这句话不是追加的动作哦，这是替换的动作
  	ReactDom.render(VDOM,document.getElementById("test"))
  
  	console.log("虚拟DOM",VDOM) //虚拟DOM Object
  	const TDOM = document.getElementById("demo")
  	console.log("真实DOM",TDOM) //真实DOM <div id="demo"></div>
  	debugger; 
  </script>
</body>
</html>
```

![截屏2022-09-24 16.02.45](VDOM.png)

输出一个Object代表虚拟DOM并不是什么高大上的东西，就是一个普通的Object的对象

```js
console.log(typeof VDOM)  //object
console.log(VDOM instanceof Object)  //true
```

关于虚拟DOM：

1. 本质是Object类型的对象（一般对象）
2. 虚拟DOM比较 "轻" ，真实DOM比较 "重" ，因为虚拟DOM是React内部在用，无需真实DOM上那么多的属性
3. 虚拟DOM最终会被React转化为真实DOM，呈现在页面上
4. Sadasdasdasdasdfdsfdsf
