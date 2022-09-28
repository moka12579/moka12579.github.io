---
title: 组件实例三大核心属性之一state
date: 2022-09-28 08:57:31
tags: react面向组件编程
categories:	
  - react面向组件编程
---

# 组件实例三大核心属性之一state

复杂组件：有状态的组件

简单组件：没有状态的组件

## 概念

人，就有一个状态

比如某次考试没考好，老师问你为什么，你就说今天的状态不太好

人的状态就影响着人的行为

组件的状态里面存着数据，状态就会驱动着页面展示

在新版React中提出了一个hooks，函数组件也可以拥有组件实例的三大核心属性

## 有一个小需求

页面上有一段话 `今天天气很炎热` 点击后切换成 `今天天气很凉爽` 再点击又变成很炎热

先在页面上展示`今天天气很炎热`

```jsx
//创建组件
class Weather extends React.Component{
  render(){
    return <h1>今天天气很炎热</h1>
  }
}
//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

写一个构造器

```jsx
//创建组件
class Weather extends React.Component{
  constructor(props) {
    super(props);
    // 一个组件有多个值
    // react的要求就是一个对象
    this.state = {isHot:true}
  }
  render(){
    return <h1>今天天气很炎热</h1>
  }
}
//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

render里就可以使用三元运算符判断

```jsx
//创建组件
class Weather extends React.Component{
  constructor(props) {
    super(props);
    // 一个组件有多个值
    // react的要求就是一个对象
    // 初始化状态
    this.state = {isHot:true}
  }
  render(){
    //读取状态
    conet {isHot} = this.state
    return <h1>今天天气很${isHot ? "炎热" : "凉爽"}</h1>
  }
}
//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

此时控制台的Component选项卡里就能显示出对应的数据

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/截屏2022-09-28 09.28.54.png)

添加点击事件

```jsx
//在外面定义一个that
let that
//创建组件
class Weather extends React.Component{
  constructor(props) {
    super(props);
    // 一个组件有多个值
    // react的要求就是一个对象
    // 初始化状态
    this.state = {isHot:true}
  }
  render(){
    //读取状态
    conet {isHot} = this.state
    //此处不能写 onclick
    //只能写 onClick
    //React将原生js所有的事件全部重写，比如 onclick --> onClick onblur --> onBlur
    //React不是原生，此处不能写"demo()"
    //如果写成{demo()} 则在渲染页面后就会调用方法，不需要点击就会输出，demo函数返回了一个undefined
    //应该写成{demo}
    return <h1 onClick={demo}}>今天天气很${isHot ? "炎热" : "凉爽"}</h1>
  }
}
function demo(){
  
}
//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

函数里修改isHot

```jsx
//创建组件
class Weather extends React.Component{
  constructor(props) {
    super(props);
    // 一个组件有多个值
    // react的要求就是一个对象
    // 初始化状态
    this.state = {isHot:true}
    //解决changeWeather中this指向问题
    this.changeWeather = this.changeWeather.bind(this)
  }
  render(){
    //读取状态
    conet {isHot} = this.state
    //此处不能写 onclick
    //只能写 onClick
    //React将原生js所有的事件全部重写，比如 onclick --> onClick onblur --> onBlur
    //React不是原生，此处不能写"demo()"
    //如果写成{demo()} 则在渲染页面后就会调用方法，不需要点击就会输出，demo函数返回了一个undefined
    //应该写成{demo}
    return <h1 onClick={this.changeWeather}}>今天天气很${isHot ? "炎热" : "凉爽"}</h1>
  }
  //changeWeather放在 Weather的原型上
  //通过Weather实例调用changeWeather时，changeWeather的this就是Weather实例
  changeWeather(){
    //由于changeWeather是做为onClick的回调，所以不是通过实例调用的，是直接调用的
    //而且类中的方法默认开启了局部的严格模式，所以changeWeather中的this为undefined
  	console.log(this) //undefined
    
    //获取原来的isHot值
    const isHot = this.state.isHot
    
    //状态不可直接更改
    //要借助一个内置的API更改
    //this.state.isHot = !isHot 这是错误的写法
    
    //一定要写对象
    //状态必须通过setState进行更新，且更新是一种合并，不是更换
    this.setState({isHot:!isHot})
    
    console.log(this.state.isHot) //布尔值已经完成切换，但是页面不会变化
    //状态里的数据不可以直接更改，虽然可以更改但是React不认可
	}
}

//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

分析 `this.changeWeather = this.changeWeather.bind(this)`

本质上是个赋值语句

等号右侧：

​	this是组件实例对象，自身没有changeWeather，会顺着原型找到了原型上的changeWeather的方法，然后调用了bind方法，传了一个this，执行完成后changeWeather方法就有了this

等号左侧：

​	给实例对象新建了一个changeWeather方法，并且改变了this指向

此时 `this.changeWeather` 就会找到自身上的changeWeather方法

类组件里render调用几次：1+n次

​	第一次是初始化的那次

​	n是状态更新的次数

changeWeather调用几次：点几次就调用几次

## state的简写方式

精简如下代码

```jsx
//创建组件
class Weather extends React.Component{
  constructor(props) {
    super(props);
    this.state = {isHot:true}
    this.changeWeather = this.changeWeather.bind(this)
  }
  render(){
    conet {isHot} = this.state
    return <h1 onClick={this.changeWeather}}>今天天气很${isHot ? "炎热" : "凉爽"}</h1>
  }
  changeWeather(){
    const isHot = this.state.isHot
    this.setState({isHot:!isHot})
	}
}

//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

state的简写方式

constructor和render的this指向没问题，changeWeather方法的this指向就有问题（因为开启了严格模式并且不是new出来的Weather实例调用的）

除了constructor和render，剩下的方法都是作为事件的回调使用



```jsx
//创建组件
class Weather extends React.Component{
  //初始化状态
  state = {isHot:true}
  render(){
    conet {isHot} = this.state
    return <h1 onClick={this.changeWeather}}>今天天气很${isHot ? "炎热" : "凉爽"}</h1>
  }
  //箭头函数没有自己的this，箭头函数里使用this时，会找外部的this作为自己的this
  //自定义方法--要用赋值语句的形式加箭头函数
  changeWeather = () => {
    const isHot = this.state.isHot
    this.setState({isHot:!isHot})
    console.log(this)//Weather的实例对象
	}
}

//渲染虚拟DOM
ReactDOM.render(<Weather/>,document.getElementById("test"))
```

