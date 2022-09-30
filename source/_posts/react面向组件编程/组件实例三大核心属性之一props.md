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

![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/anli.png)

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

### 批量传递props

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

### 对props进行限制

需要对person组件传递的标签属性类型限制

进行必要性的限制，对性别提供默认值

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
        <li>年龄：{age+1}</li>
      </ul>
    )
  }
}
//只负责这样写，React帮你限制
Person.propTypes = {
  //name就被限制，只能写字符串类型
  //在React的15版本之前PropTypes可以使用，但是16版本开始这样就弃用
  //name:React.PropTypes.string
  //16版本之后应该这样写
  //引入prop-types，用于对组件标签属性进行限制
  name: PropTypes.string.isRequried // 限制name必传，且为字符串
  sex: PropStypes.string // 限制sex为字符串
  age: PropStypes.number // 限制age为数值
}
//指定默认的标签属性值
Person.defaultProps = {
  sex:"男", // 默认性别为男
  age: 18 // 默认年龄为18
}
//渲染组件
ReactDOM.render(<Person name="tom" age={18} sex="女"/>,document.getElementById("test"))
ReactDOM.render(<Person name="jerry" age={19} sex="男"/>,document.getElementById("test1"))
//此时把name改为数字，控制台就会报错，会保证页面的正常显示
//不传name同样也会报错
//不传性别。页面上性别就是不男不女
//年龄不传默认值就是18
ReactDOM.render(<Person name={100}/>,document.getElementById("test2"))
```

下载： {% link prop-type https://react-1300475487.cos.ap-chengdu.myqcloud.com/16.8.4/prop-types.js %}

### 简写props

将propTypes和defaultProps放到类自身里面

```jsx
class Person extends React.Component {
  render(){
    let {name,age,sex} = this.props
    return (
    	<ul>
        <li>姓名：{name}</li>
        <li>性别：{sex}</li>
        <li>年龄：{age+1}</li>
      </ul>
    )
  }
  //只负责这样写，React帮你限制
  static propTypes = {
    name: PropTypes.string.isRequried 
    sex: PropStypes.string 
    age: PropStypes.number 
  }
  //指定默认的标签属性值
  static defaultProps = {
    sex:"男", 
    age: 18 
  }
}
//渲染组件
ReactDOM.render(<Person name="tom" age={18} sex="女"/>,document.getElementById("test"))
ReactDOM.render(<Person name="jerry" age={19} sex="男"/>,document.getElementById("test1"))
```

## 构造器与props

之前定义Person组件没有构造器，现在加上构造器

```jsx
class Person extends React.Component {
  //可以省略构造器，但是写了构造器后不接也不在super里传props，就无法在构造器中用实例获取props
  //构造器是否接收props，是否传递给super，取决于构造器里是否需要通过this访问props
  constructor(props){
    console.log(props)// Person{name:"tom",sex:18,age:"女"}
  }
  render(){
    let {name,age,sex} = this.props
    return (
    	<ul>
        <li>姓名：{name}</li>
        <li>性别：{sex}</li>
        <li>年龄：{age+1}</li>
      </ul>
    )
  }
  //只负责这样写，React帮你限制
  static propTypes = {
    name: PropTypes.string.isRequried 
    sex: PropStypes.string 
    age: PropStypes.number 
  }
  //指定默认的标签属性值
  static defaultProps = {
    sex:"男", 
    age: 18 
  }
}
ReactDOM.render(<Person name="tom"/>,document.getElementById("test"))
```

在 React 组件挂载之前，会调用它的构造函数。在为 React.Component 子类实现构造函数时，应在其他语句之前调用 `super(props)`。否则，`this.props` 在构造函数中可能会出现未定义的 bug。

通常，在 React 中，构造函数仅用于以下两种情况：

- 通过给 `this.state` 赋值对象来初始化{% link 内部 state https://zh-hans.reactjs.org/docs/state-and-lifecycle.html %}。
- 为{% link 事件处理函数 https://zh-hans.reactjs.org/docs/handling-events.html %}绑定实例
