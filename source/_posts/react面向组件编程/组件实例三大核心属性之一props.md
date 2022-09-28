---
title: 组件实例三大核心属性之一props
date: 2022-09-28 19:16:55
tags: react面向组件编程
categories:	
  - react面向组件编程
---

# 组件实例三大核心属性之一props

## props的基本使用

做这么一个案例

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/截屏2022-09-28 19.19.01.png)

把人的信息展示到页面上，两个人的形式都是展示姓名，性别，年龄

```jsx
// 创建组件
class Person extends React.Component {
  render(){
    // console.log(this) 输出Person的实例对象，实例对象里就有props，但是一个空对象
    let {name,age,sex} = this.props
    return (
    	<ul>
        <li>姓名：{name}</li>
        <li>性别：{sex}</li>
        <li>年龄：{age}</li>
      </ul>
    )
  }
}
//渲染组件
ReactDOM.render(<Person name="tom" age="18" sex="女"/>,document.getElementById("test"))
ReactDOM.render(<Person name="jerry" age="19" sex="男"/>,document.getElementById("test1"))
ReactDOM.render(<Person name="小王" age="20" sex="女"/>,document.getElementById("test2"))
// console.log(this) 输出Person的实例对象，实例对象里就有props，值是{name:"tom",age:"18",sex:"女"}
```

## props的高级使用

如果人的信息特别多，渲染组件就会显得很长

```jsx
const p = {name:"老刘",age:18,sex:"女"} //假设这是服务器返回的数据

//渲染组件就需要这样写
ReactDOM.render(<Person name={p.name} age={p.age} sex={p.sex}/>,document.getElementById("test2"))

//简写的方式
//就是上面那个的语法糖
//前提是服务器返回的数据和组件里结构赋值要一致
ReactDOM.render(<Person {...p}/>,document.getElementById("test2"))
```

bebel加react可以让展开运算符展开一个属性，但是不能随意使用，仅仅是用于标签属性的传递

