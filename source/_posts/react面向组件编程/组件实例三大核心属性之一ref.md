---
title: 组件实例三大核心属性之一ref
date: 2022-10-03 15:09:48
tags: react面向组件编程
categories:	
  - react面向组件编程
---

# 组件实例三大核心属性之一ref

## 字符串形式的ref

做一个小效果

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/ref效果.png)

左侧输入框输入值以后点击中间的按钮，弹窗显示输入的内容

右侧输入框失去焦点也会弹窗输入的内容

ref就相当于原生js里的id

```jsx
//创建组件
class Demo extends React.Component{
  //展示左侧输入框的数据
  showData = () => {
    
    //原生写法
    //const input = document.getElementById("input1")
    //alert(input.value)
    
    //console.log(this) // Demo组件的实例对象
    //console.log(this.refs.input1)//当按钮点击后则拿到第一个input的节点，收集到的是虚拟DOM转成真实DOM后的节点
    
    const {input1} = this.refs
    alert(input1.value)
  }
  showData2 = () => {
    const {input2} = this.refs
    alert(input2.value)
  }
  render(
  	return (
    	<div>
     		<input ref="input1" type="text" placeholder="点击按钮提示数据"></input>
       	<button  onClick={this.showData}>点我提示左侧的数据</button>
        <input ref="input2" onBlur={showData2} type="text" placeholder="失去焦点提示数据"></input>
      </div>	
    )
  )
}

ReactDOM.render(<Demo/>,document.getElementById("test"))
```

字符串类型的ref即将被废弃 {% link 链接 https://react.docschina.org/docs/refs-and-the-dom.html#legacy-api-string-refs %}

字符串类型的ref存在一定的效率问题

## 回调函数形式的ref

```jsx
//创建组件
class Demo extends React.Component{
  //展示左侧输入框的数据
  showData = () => {
    const {input1} = this
    alert(input1.value)
  }
  showData2 = () => {
    const {input2} = this
    alert(input2.value)
  }
  render(
  	return (
    	<div>
        <!-- c 就是ref所在的节点 -->
     		<input ref={c => this.input1 = c} type="text" placeholder="点击按钮提示数据"></input>
       	<button onClick={this.showData}>点我提示左侧的数据</button>
        <input ref={c => this.input2 = c} onBlur={showData2} type="text" placeholder="失去焦点提示数据"></input>
      </div>	
    )
  )
}

ReactDOM.render(<Demo/>,document.getElementById("test"))
```

回调执行次数的问题

```jsx
//创建组件
class Demo extends React.Component{
  state = {isHot:true}
  showData = () => {
    const {input1} = this
    alert(input1.value)
  }
  changeWeather = () => {
    const {isHot} = this.state
    this.setState({isHot:!isHot})
  }
  render(
  	return (
      const {isHot} = this.state
    	<div>
        <h2>今天天气很{isHot?"炎热":"凉爽"}</h2>
     		<input ref={c => {this.input1 = c;console.log("@",c)}} type="text" placeholder="点击按钮提示数据"></input>
       	<button onClick={this.showData}>点我提示输入的数据</button>
				<button onClick={this.changeWeather}>点我切换天气</button>
      </div>	
    )
  )
}

ReactDOM.render(<Demo/>,document.getElementById("test"))
```

肯定会调用一次

官方说明：{% link 关于回调 refs 的说明 https://react.docschina.org/docs/refs-and-the-dom.html#caveats-with-callback-refs %}

当加入切换天气功能后，`console.log("@",c)` 会输出两行 `@  null` 和  `@  节点元素`

当更新数据时，render就会重新调用，为了有一个清空的动作，ref里的函数就会收到一次null，一次真实的节点

重新写一个input，ref写成类绑定的形式

```jsx
//创建组件
class Demo extends React.Component{
  state = {isHot:true}
  showData = () => {
    const {input1} = this
    alert(input1.value)
  }
  changeWeather = () => {
    const {isHot} = this.state
    this.setState({isHot:!isHot})
  }
  saveInput = c => {
    this.input1 = c;
    console.log("@",c)}
  render(
  	return (
      const {isHot} = this.state
    	<div>
        <h2>今天天气很{isHot?"炎热":"凉爽"}</h2>
				{/*这种形式避免了那两行输出 */}
				{/* 内联的方式写的很多 */}
     		<input ref={this.saveInput} type="text" placeholder="点击按钮提示数据"></input>
       	<button onClick={this.showData}>点我提示输入的数据</button>
				<button onClick={this.changeWeather}>点我切换天气</button>
      </div>	
    )
  )
}

ReactDOM.render(<Demo/>,document.getElementById("test"))
```

## createRef API

{% link 官方链接 https://react.docschina.org/docs/refs-and-the-dom.html#creating-refs %}

返回一个容器，该容器专人专用，只能存一个。后放进去的几点就会顶掉之前存进去的

用几个ref，就需要创建几个ref容器

React最推荐的方式

```jsx
//创建组件
class Demo extends React.Component{
  /*
  	React.createRef返回一个容器，该容器可以存储被ref所标识的节点
  */
  myRef = React.createRef()
  myRe2 = React.createRef()
  //展示左侧输入框的数据
  showData = () => {
    console.log(this.myRef) // 输出的是一个对象，对象里包含当前被标识的节点
    alert(this.myRef.current.value)
  }
  showData2 = () => {
    alert(this.myRef2.current.value)
  }
  render(
  	return (
    	<div>
        {/* 会将当前节点存入myRef这个容器 */}
     		<input ref={this.myRef} type="text" placeholder="点击按钮提示数据"></input>
       	<button onClick={this.showData}>点我提示输入的数据</button>
       <input onBlur={this.showData2} ref={this.myRef2} type="text" placeholder="失去焦点提示数据"></input>
      </div>	
    )
  )
}

ReactDOM.render(<Demo/>,document.getElementById("test"))
```

## 总结

1. 字符串形式的ref是最简单的，条件允许的情况下可以使用字符串形式的ref，但是能避免就尽量避免
2. 回调形式的ref不会自动收集，稍微麻烦一点
3. 类绑定形式的就是一个扩展，其实一直在用的就是回调形式的ref
4. createRef是最麻烦的一种，目前react最推荐的一种

