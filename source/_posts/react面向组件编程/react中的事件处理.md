---
title: react中的事件处理
date: 2022-10-03 16:18:13
tags: react面向组件编程
categories:	
  - react面向组件编程
---

# react中的事件处理

还是之前的案例

1. 通过onxxx属性绑定事件处理函数（注意大小写）
   1. react中使用的是自定义（合成）事件，而不是使用原生DOM事件 —— 为了更好的兼容性
   2. React中的事件是通过事件委托方式处理的 —— 为了高效
2. 通过event.target得到发生事件的DOM元素对象 —— {% link 不要过度使用ref https://react.docschina.org/docs/refs-and-the-dom.html#dont-overuse-refs %}

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
    alert(event.target.value)
  }
  render(
  	return (
    	<div>
        {/* 会将当前节点存入myRef这个容器 */}
     		<input ref={this.myRef} type="text" placeholder="点击按钮提示数据"></input>
       	<button onClick={this.showData}>点我提示输入的数据</button>
       <input onBlur={this.showData2} type="text" placeholder="失去焦点提示数据"></input>
      </div>	
    )
  )
}

ReactDOM.render(<Demo/>,document.getElementById("test"))
```

