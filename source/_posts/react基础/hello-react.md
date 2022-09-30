---
title: hello-react
date: 2022-09-23 09:09:11
tags: react
categories: 	
 - react基础
---

# React入门

## React官网

- 英文官网 {% link react https://reactjs.org %}
- 中文官网 {% link react https://react.docschina.org %}

# React的基本使用

- 推荐网站 {% link codepen https://codepen.io/pen?&editors=0010&layout=left %}
- `codepen` 是一个在线的代码编辑器的网站，可以在线测试使用React

## 效果

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/react效果.png)

## 相关js库

### 	本文依据React 16.8.4所写

当年在学习jQuery就是在html里引入jQuery.js



####  	16.8.4版本下载：

​			babel.min.js {% link 点击下载 https://react-1300475487.cos.ap-chengdu.myqcloud.com/16.8.4/babel.min.js %}

​			react-dom.development.js {% link 点击下载 https://react-1300475487.cos.ap-chengdu.myqcloud.com/16.8.4/react-dom.development.js %}

​			react.development.js {% link 点击下载 https://react-1300475487.cos.ap-chengdu.myqcloud.com/16.8.4/react.development.js %}

#### 	18.2.0版本下载：

​		babel.min.js {% link 点击下载 https://react-1300475487.cos.ap-chengdu.myqcloud.com/18.2.0/babel.min.js %}

​		react-dom.development.js {% link 点击下载 https://react-1300475487.cos.ap-chengdu.myqcloud.com/18.2.0/react-dom.development.js %}

​		react.development.js {% link 点击下载 https://react-1300475487.cos.ap-chengdu.myqcloud.com/18.2.0/react.development.js %}

##### babel:

​	es6新语法的时候有些浏览器不认识，就需要babel将es6转es5

​	js模块化的时候引入的单词 `import` 浏览器不认识也是需要babel将es6转es5

​	babel第二种用法：

​		jsx转换为js

​		jsx不是新的语言，只是在js的基础上提出新的要求和语法，不是很多，js基础不错就能很轻松的掌握

​		浏览器不认识jsx，就需要babel转换jsx为js

##### react.development.js

​	React的核心库

##### react-dom.development.js

​	React的扩展库，扩展React的操作DOM



# hello-React

1. 引入React的js文件

2. 新建一个hello_React.html

3. 开始编码

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
     </script>
   </body>
   </html>
   ```

4. 运行效果

   1. ![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/react效果.png)

   2. 控制台有一些警告

      ![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/warn.png)

      第一个输出是因为没有在浏览器安装开发者工具

      浏览器现翻译jsx，当虚拟DOM过多时，浏览器会白屏一段时间

      现在学习基本语法，这个警告可以忽略，毕竟不是按照人家的标准写的
      
      
