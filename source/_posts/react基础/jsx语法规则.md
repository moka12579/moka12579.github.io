---
title: jsx语法规则
date: 2022-09-24 16:10:42
tags: react
categories:

- react基础

---

# jsx语法规则

## 先了解一下xml

XML早起用于存储和传输数据

```xml
<student>
    <name>Tom</name>
    <age>19</age>
</student>
```

后来就逐渐不用XML了，开始使用JSON了

XML感觉结构比内容都多

JSON方式：

```json
{
  name: "TOM",
  age: 19
}
```

JS内置JSON对象，有parse和stringfy可以互相转换

XML现在在微信的公众号与开发者服务器之前还在使用

## jsx

1. 全称：JavaScript XML

2. React定义的一种类似于 XML 的js扩展语法：js + XML
3. 本质是 React.createElement(component,props,...childer) 方法的语法糖
4. 作用：简化创建虚拟DOM
    1. 写法：`let vdom = <h1>Hello JSX!</h1> `
    2. 注意1: 它不是字符串，也不是 HTML/XML 标签
    3. 注意2: 它最终产生的就是一个JS对象
5. 标签名：任意HTML标签或其它标签

### 案例

```jsx
    //1. 创建虚拟DOM
const VDOM = (// 此处一定不要写引号，因为不是字符串
    <h2 id="atguigu">
        <span>hello,react</span>
    </h2>
)
//2. 渲染虚拟DOM到页面
// ReactDOM.render(虚拟DOM,容器)
// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
// 注意这句话不是追加的动作哦，这是替换的动作
ReactDom.render(VDOM, document.getElementById("test"))
```

效果

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/jsx1.png)

## 语法规则

1. 定义虚拟DOM时，不要写引号

2. 标签中混入JS表达式时，要用{}

```jsx
//读取变量
let myId = 'aTgUiGu'
let myData = 'HeLlo,rEaCt'
//1. 创建虚拟DOM
const VDOM = (// 此处一定不要写引号，因为不是字符串
    <h2 id={myId.toLowerCase()}>
       <span>{myData.toLowerCase()}}</span>
    </h2>
)
//2. 渲染虚拟DOM到页面
// ReactDOM.render(虚拟DOM,容器)
// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
// 注意这句话不是追加的动作哦，这是替换的动作
ReactDom.render(VDOM, document.getElementById("test"))
```




3. 样式的类名指定不要用class，要用className

```jsx
//css样式
<style>
    .title{
        background:orange;
        width:200px;
    }
</style>
//读取变量
let myId = 'aTgUiGu'
let myData = 'HeLlo,rEaCt'
//1. 创建虚拟DOM
const VDOM = (// 此处一定不要写引号，因为不是字符串
    // <h2 class='text' id={myId.toLowerCase()}>
    //此时会报错 Invalid DOM property `class`. Did you mean `className`?
        
    <h2 className='text' id={myId.toLowerCase()}>
       <span>{myData.toLowerCase()}}</span>
    </h2>
)
//2. 渲染虚拟DOM到页面
// ReactDOM.render(虚拟DOM,容器)
// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
// 注意这句话不是追加的动作哦，这是替换的动作
ReactDom.render(VDOM, document.getElementById("test"))
```




4. 内联样式，要用 `style={{key:value}}` 的形式写

```jsx
   //css样式
<style>
    .title{
        background:orange;
        width:200px;
    }
</style>
//读取变量
let myId = 'aTgUiGu'
let myData = 'HeLlo,rEaCt'
//1. 创建虚拟DOM
const VDOM = (// 此处一定不要写引号，因为不是字符串

    // <h2 class='text' id={myId.toLowerCase()}>
    //此时会报错 Invalid DOM property `class`. Did you mean `className`?

    //font-size这种多单词的要用小驼峰的形式写
    <h2 className='text' style={{color: "white", fontSize: "30px"}} id={myId.toLowerCase()}>
       <span>{myData.toLowerCase()}}</span>
    </h2>
)
//2. 渲染虚拟DOM到页面
// ReactDOM.render(虚拟DOM,容器)
// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
// 注意这句话不是追加的动作哦，这是替换的动作
ReactDom.render(VDOM, document.getElementById("test"))
```




5. 只有一个根标签

```jsx
   //1. 创建虚拟DOM
const VDOM = (// 此处一定不要写引号，因为不是字符串
    <div>
       <h2 id="atguigu">
          <span>HeLlo,rEaCt</span>
       </h2>
       <h2 id="ATGUIGU">
          <span>HeLlo,rEaCt</span>
       </h2>
    </div>

)
//2. 渲染虚拟DOM到页面
// ReactDOM.render(虚拟DOM,容器)
// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
// 注意这句话不是追加的动作哦，这是替换的动作
ReactDom.render(VDOM, document.getElementById("test"))
```




6. 标签必须闭合

```jsx
//1. 创建虚拟DOM
const VDOM = (// 此处一定不要写引号，因为不是字符串
    // 此时会报错
    // <input type="text">
         
    <input type="text"/>//或者<input type="text"></input>
)
//2. 渲染虚拟DOM到页面
// ReactDOM.render(虚拟DOM,容器)
// React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
// 注意这句话不是追加的动作哦，这是替换的动作
ReactDom.render(VDOM, document.getElementById("test"))
```




7. 标签首字母

   
   
   
      1. 若小写字母开头，则将该标签转为HTML中同名元素，若HTML中无该标签对应的同名元素，则报错
         ```jsx
         //1. 创建虚拟DOM
         const VDOM = (// 此处一定不要写引号，因为不是字符串
           <good>123</good>
           //虽然页面能显示123，但是控制台报错
           //The tag <good> is unrecognized in this browser. If you meant to render a React component, start its name with an uppercase letter.	
           //React将写的html标签转换为html时，如果小写字母的标签，就会转换为html里的同名标签，
           //比如写的span，就会转换为html里的span标签
         )
         //2. 渲染虚拟DOM到页面
         // ReactDOM.render(虚拟DOM,容器)
         // React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
         // 注意这句话不是追加的动作哦，这是替换的动作
         ReactDom.render(VDOM, document.getElementById("test"))
         ```
         
         
         
      1. 若大写字母开头，React就去渲染对应的组件，若组件没有定义，则报错
   
         ```jsx
         //1. 创建虚拟DOM
         const VDOM = (// 此处一定不要写引号，因为不是字符串
           <Good>123</Good>
           //页面不显示，直接报错
         )
         //2. 渲染虚拟DOM到页面
         // ReactDOM.render(虚拟DOM,容器)
         // React没有提供选择器，只能使用document，整个也就这里需要document，没有这个写不下去
         // 注意这句话不是追加的动作哦，这是替换的动作
         ReactDom.render(VDOM, document.getElementById("test"))
         ```
         
         
